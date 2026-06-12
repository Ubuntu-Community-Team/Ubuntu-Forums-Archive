---
title: "xhost security"
date: 2006-02-05
forum: General Help
---

### Post by Gowator on 2006-02-05
I have a ssh session open to another machine with xhost + explicitly opening that machine and the DISPLAY ENVVAR set correctly but it keeps saying 
```

xterm Xt error: Can't open display: 192.168.1.10:0.0
```

Can anyone please say what I am doing wrong ?

---

### Post by Gowator on 2006-02-05
[QUOTE=Gowator]I have a ssh session open to another machine with xhost + explicitly opening that machine and the DISPLAY ENVVAR set correctly but it keeps saying 
```

xterm Xt error: Can't open display: 192.168.1.10:0.0
```

Can anyone please say what I am doing wrong ?[/QUOTE]


Hmm seems Ubuntu ships wih the /etc/X11/gdm/gdm.conf set with nolisten (weird for the most insecure distro I have ever seen) but there it is...  same goes for the kdm.conf for kubuntu users ???

Having installed a rootkit with the /etc/sudoers file (in the interests of people being too stupid to have a root password) it seems strange to disable the xserver listening on tcp ???

---

### Post by WARnux on 2008-06-24
How are you connecting with ssh?

ssh -X -p 22 userName@hostName

I'm not sure you need/should use xhost +.  It can be a major security risk.

---

