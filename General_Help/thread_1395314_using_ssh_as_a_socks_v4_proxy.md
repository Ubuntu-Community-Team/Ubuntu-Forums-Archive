---
title: "using ssh as a socks v4 proxy"
date: 2010-01-31
forum: General Help
---

### Post by 26venger on 2010-01-31
as we all know ssh has an huge number of uses. in this tutorial i will be instructing **you how to use ****ssh as a socks proxy** in your browser or any other application that can be configured for that matter. it will also send your traffic through an encrypted tunnel.

**Part 1**

to start off we will be using the -D switch which is an overlooked but extremely useful feature of ssh. the -D switch combines itself with a specified port, encrypts the traffic going down that port, and decrypts it on the other side.

for example, to set up a socks 4 proxy from port 8080 use this command

ssh -D 8080 remoteserver

by the way it sends traffic through the remote server 
**Part 2**

for part 2 i will be configuring mozilla

all that you need to do now is configure your application. in mozilla firefox. go to preferences>advanced>proxies select manual proxy configuration and type localhost as the SOCKS host. enter the port you gave to the -D switch and make sure you check the SOCKSv4 button. click ok and your finished.

this is my first tutorial ive written on ubuntuforums so please tell me if you liked it:)

---

