---
title: "Error mounting ftp"
date: 2012-05-09
forum: General Help
---

### Post by snovik on 2012-05-09
I am trying to mount a hdd connected to router via ftp. So I issue

curlftpfs hdd.routerlogin.net/USB_Storage/ ~/Cloud/

and receive "Error connecting to ftp: Got a 230 ftp-server response when 220 was expected"

Well, the code 230 actually means "User logged in, proceed. This status code appears after the client sends the correct password. It indicates that the user has successfully logged on."

So how can I mount an ftp as folder?

---

### Post by sharkllama on 2012-08-09
I have (what I can only assume is) the exact same problem here.  I have yet to find any other (useful) information on the web.  It seems that without a user/pass for the ftp filesystem that curl will fail to mount the device. Very strange ...

---

