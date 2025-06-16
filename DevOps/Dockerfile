### BASE IMAGE
FROM alpine:3.19.1

### SETTING ENVIRONMENT VARIABLES.
ENV http_proxy=$http_proxy
ENV https_proxy=$https_proxy
ENV no_proxy=localhost,127.0.0.1,afservice,nefservice,cntfservice

### UPGRADE THE IMAGE.
RUN apk update && apk add bash

### INSTALL PACKAGES
RUN apk add apk-tools busybox
RUN apk add --no-cache wget libc6-compat libstdc++ net-tools nmap
RUN apk add --no-cache gcompat
RUN ln -s /lib/libc.so.6 /usr/lib/libresolv.so.2

### CREATE USER
RUN adduser -D nabstractnef

## Permission
RUN chown -R nabstractnef:nabstractnef /home/nabstractnef

# COPY FILES
COPY ./nef /home/nabstractnef/
COPY ./entrypoint.sh /home/nabstractnef/

# PERMISSION GRANT
RUN chmod -R 777 /home/nabstractnef/nef
RUN chmod -R 777 /home/nabstractnef/entrypoint.sh

### SET THE NON-ROOT USER AS THE DEFAULT USER.
USER nabstractnef

### SET THE WORKING DIRECTORY.
WORKDIR /home/nabstractnef

### ENTRYPOINT
CMD ["/home/nabstractnef/entrypoint.sh"]
