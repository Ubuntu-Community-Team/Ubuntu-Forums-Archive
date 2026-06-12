---
title: "xorg.cong issue"
date: 2006-06-12
forum: General Help
---

### Post by wizzkid on 2006-06-12
Hi! I am having an issue on my xorg.conf. I installed 915resolution so I could get desired resolution for my DELL Inspiron 700m. My problem was on the login screen, its too big when I bring my mouse cursor to the end/ edge of the screen the login screen moves. but when Im in the OS proper, the resolution is good, and is at 1240x800

And also, xorg.conf automatically change its content, thats why the login screen look so big, i dont know which to fix.. but here's my xorg.conf [http://leeph.net/pastebin/xorg.conf](http://leeph.net/pastebin/xorg.conf)

My original xorg.conf is [http://leeph.net/pastebin/xorg.conf.orig](http://leeph.net/pastebin/xorg.conf.orig) which is good even in login screen. however, after 3 reboots, it automatically changes to [http://leeph.net/pastebin/xorg.conf](http://leeph.net/pastebin/xorg.conf)

Also, xorg.conf creates another xorg.conf automatically but named to xorg.conf.1 xorg.conf.2 xorg.conf.3 with the content of [http://leeph.net/pastebin/xorg.conf.orig](http://leeph.net/pastebin/xorg.conf.orig)

why this happen? 

Any suggestions and reponse would be highly appreciated,

Thanks.

---

### Post by wizzkid on 2006-06-14
any? :)

---

### Post by dresnu on 2006-06-14
Try running```
sudo dpkg-reconfigure xserver-xorg
```

---

