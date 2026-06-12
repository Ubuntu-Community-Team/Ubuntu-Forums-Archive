---
title: "/etc/rc.d question"
date: 2010-03-03
forum: General Help
---

### Post by danrche on 2010-03-03
Hello all,

 what does the S99 and K01 mean or stand for in the /etc/rc.d/rc5.d folder? 

I know that it's used to point to scripts to start and stop services and applications on boot at different run-levels (rc5.d = runlevel 5) but I don't know what they all start with K and a number, and S and a number. I'm just curious.

Also, does it make a difference what I label it since it's a symbolic link?

---

### Post by spiderbatdad on 2010-03-03
not technically sure but I think of Start and Kill. If you edit the file name in all the runlevels changing S to K the process will not run at startup. I don't think is the supported method at present, however. Instead use upstart and update-rc.d whose actual scripts are in /etc/init.d

---

### Post by danrche on 2010-03-03
hum, I usually don't edit these files either, most of the packages I use will do that for me or have a pretty GUI interface to make it work. But I've recently turned up a LAMP server for work and part of the instructions was to put ln -s /opt/lampp/lampp K99lampp  and S01lampp into rc5.d to make it auto start. I'm not really sure what the 1st 3 letters/numbers mean but get the idea of the rc.d files. 


I thought kill and start as well. I only ask out of curiosity. my Lampp server starts and shutsdown on it's own like it's supposed to so I'm sure it's working. 

I turned Lampp up on a RHEL 5 box, but I like this forum which is why I posted here.

---

### Post by Iowan on 2010-03-03
> **danrche said:**
>  what does the S99 and K01 mean or stand for in the /etc/rc.d/rc5.d folder? Start and kill respectively. The example would be the last to start or the first to "die".

---

