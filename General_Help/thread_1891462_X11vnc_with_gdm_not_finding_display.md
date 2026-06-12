---
title: "X11vnc with gdm not finding display"
date: 2011-12-05
forum: General Help
---

### Post by duindain on 2011-12-05
Hi Im trying to get the gdm login manager to work with x11vnc
ive tried all the usual suspects
```

-auth /var/gdm/:0.Xauth
-auth /var/lib/gdm/:0.Xauth
-auth /var/run/lightdm/root/:0
-auth guess
-findauth
-env FD_XDM=1 -auth guess

```
these are suggested by many help pages with no luck on any of them
ps wwwaux | grep auth shows
```

root      2236  0.0  0.0  29996   880 ?        Ss   Dec04   0:01 /usr/sbin/vmware-authdlauncher
myUserName 21349  0.0  0.0  12048   896 pts/2    S+   06:02   0:00 grep --color=auto auth

```

Ive had this working with lxdm with no issues by changing to one of the auth lines revealed from the above command but there doesnt seem to be one for gdm

This is the error from the logfile
```

06/12/2011 05:50:13 passing arg to libvncserver: -desktop
06/12/2011 05:50:13 passing arg to libvncserver: MyPCName:0
06/12/2011 05:50:13 passing arg to libvncserver: -rfbauth
06/12/2011 05:50:13 passing arg to libvncserver: /home/MyUserName/.vnc/passwd
06/12/2011 05:50:13 passing arg to libvncserver: -rfbversion
06/12/2011 05:50:13 passing arg to libvncserver: 3.6
06/12/2011 05:50:13 passing arg to libvncserver: -permitfiletransfer
06/12/2011 05:50:13 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 21211
06/12/2011 05:50:13 XOpenDisplay(":0") failed.
06/12/2011 05:50:13 Trying again with XAUTHLOCALHOSTNAME=localhost ...

06/12/2011 05:50:13 ***************************************
06/12/2011 05:50:13 *** XOpenDisplay failed (:0)

```

Im using this command to start x11vnc at the moment
```

sudo /usr/bin/x11vnc -rc ~/.x11vncrc~ -auth -auth /var/lib/gdm/:0.Xauth - display :0 -o /var/x11vnc.log

```

---

### Post by phidia on 2011-12-05
Is the client/computer you are using to connect to your server or remote computer also using linux? I'm just offering ideas that may inspire you btw but you can look at the vnc guide [here]("http://news.metaparadigma.de/linux-setting-up-a-debian-vnc-server-237/") (which I've used) but perhaps more specific to the error you are getting is the FAQ help at [this website]("http://www.karlrunge.com/x11vnc/faq.html#faq-xperms"). Good luck.

---

### Post by krunge on 2011-12-06
Is there an X server even running?  x11vnc needs to attach to an already running X server.  Try this to start looking if one is running:
```

ps wwaux | grep X

```
If there is none you will need to configure your system to start one (gdm init script is a common way.)

---

### Post by duindain on 2011-12-07
Ive managed to resolve this for now thankyou for your help :)

the default login manager hadn't been set even though i selected gdm after uninstalling ldxe so I had to manually edit that file

then the gdm authorisation poped up with the ps wwwaux | grep auth command and i can use that to attach to the running display and the -create option seems to be working so if noone is logged in i get to the login screen and can login sucsessfully

Thanks again :)

---

