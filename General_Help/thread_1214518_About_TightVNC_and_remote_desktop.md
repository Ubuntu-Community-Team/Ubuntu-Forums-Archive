---
title: "About TightVNC and remote desktop"
date: 2009-07-16
forum: General Help
---

### Post by MasterH on 2009-07-16
Hi
I am new to ubuntu. I have server use ubuntu 8.10 server ver. I have install ubuntu-desktop and TightVNCserver on it but when I connect the server's remote desktop it fail. I search this problem on google the answer is turn on the remote desktop 
but I only can use ssh to connect my server How can I turn on the remote desktop with ssh?
Thank you!

---

### Post by cariboo on 2009-07-16
Make sure the TightVNCServer is running on the server. Ssh into your server and at the prompt type:

```
ps ax | grep vnc
```

The above command should tell you whethter the server is running.

---

### Post by MasterH on 2009-07-16
8579 pts/0    S+     0:00 grep vnc
10022 ?        S      0:01 Xtightvnc :1 -desktop X -auth /home/masteradmin/.Xauthority -geometry 1024x768 -depth 24 -rfbwait 120000 -rfbauth /home/masteradmin/.vnc/passwd -rfbport 5901 -fp /usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /usr/X11R6/lib/X11/rgb
10026 ?        S      0:00 /bin/sh /home/masteradmin/.vnc/xstartup

this is the result !

---

