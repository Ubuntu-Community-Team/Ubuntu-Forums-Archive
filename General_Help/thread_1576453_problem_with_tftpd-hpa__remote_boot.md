---
title: "problem with tftpd-hpa / remote boot"
date: 2010-09-17
forum: General Help
---

### Post by ibrabeicker on 2010-09-17
so I'm doing a project of diskless ubuntu following this tutorial 

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

I have a pxelinux.0 that is at /tftpboot that the client should read and start the boot, but at first I was getting the message "host unreachable (port unreachable)", then I remembered reading somewhere that all ports in ubuntu comes closed, so I did a little research and used this command to open the 69 port

```
sudo iptables -A INPUT -p udp --dport 69 -j ACCEPT
```

but now the open operation of "pxelinux.0" time out because my computer (the server) does not respond.
tftpd-hpa find the file, receive the open request but does not respond
does tftpd-hpa use another port to answer the request?



my server IP is 192.168.2.1 and my /etc/default/tftpd-hpa  conf is this 

```
# /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure"
RUN_DAEMON="yes"
OPTIONS="-l -s /tftpboot/"
```

---

### Post by ibrabeicker on 2010-09-17
bump for help

---

