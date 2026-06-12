---
title: "GDM prob"
date: 2010-03-05
forum: General Help
---

### Post by illbashu on 2010-03-05
GDM kept saying could not find /etc/gdm/custom.conf so I reinstalled GDM (sudo aptitude reinstall gdm) and now it's loading but the background but it wont load the login window and it still says it can't find custom.conf. How do I fix this?

BTW I don't know if this is related but a notification poped up and said that power manager wasn't installed. I did

sudo aptitude install gnome-power-manager and it seems to be installed. :/

---

### Post by illbashu on 2010-03-05
Logs.

---

### Post by rnerwein on 2010-03-05
hi
it ain't looks like a gdm problem. i have a look to your lockfiles. your nvidia graphic card driver is gone. did you do a kernel update ? then you have to reconfigure ( or reinstall your nvidia driver ).
the first you can try is --> boot into recovery mode. --> cd /etc/X11 --> mv xorg.conf xorg.conf.your_name. --> reboot.
this should cause the system to use the native graphic drivers ( i hope so ). then you can reconfigure your nvidia driver using a GUI
good luck
ciao

---

### Post by illbashu on 2010-03-05
> **rnerwein said:**
> hi
it ain't looks like a gdm problem. i have a look to your lockfiles. your nvidia graphic card driver is gone. did you do a kernel update ? then you have to reconfigure ( or reinstall your nvidia driver ).
the first you can try is --> boot into recovery mode. --> cd /etc/X11 --> mv xorg.conf xorg.conf.your_name. --> reboot.
this should cause the system to use the native graphic drivers ( i hope so ). then you can reconfigure your nvidia driver using a GUI
good luck
ciao

I'm using the drivers from Nvidia.com and I reinstalled it, didn't make a difference. I'll try what you said though.

Checked the log and it seems to have fixed the driers prob but it's still just loading the background and mouse, the actual login box isn't loading.

It's saying it can't find custom.conf. I'll see if I can find my camera so I can take a picture.

I'll just enable automatic login for now.

---

### Post by illbashu on 2010-03-05
I think I'll just reinstall ubuntu. Does anyone know if there is a way to just install the Base and link all the user and home data to it?

---

### Post by illbashu on 2010-03-06
bump!

---

### Post by illbashu on 2010-03-06
Well not I completely removed and reinstalled Nvidia drivers there is clearly no probs with the drivers. GDM loads up the background and mouse then the sound comes on but the actual loginbox doesn't show up. Here is a screen. 

[http://img717.imageshack.us/img717/1707/dsc00303w.jpg](http://img717.imageshack.us/img717/1707/dsc00303w.jpg)
GDM login screen. 

Another prob I'm having is that I can't use the the terminal. 
[http://img714.imageshack.us/img714/1415/dsc00307c.jpg](http://img714.imageshack.us/img714/1415/dsc00307c.jpg)

---

### Post by rnerwein on 2010-03-06
hi again
you have reinstalled the nvidia driver. did you try also:
 nvidia-xconfig ( packages are available with apt-get --> nvidia-glx-173 , nvidia-glx-185 and     
 nvidiaglx-96
try also: nvidia-settings ( apt-get install nvidia-settings )
and the last:  nautilus -p && nautilus ( the option -p is not in the manual pages on karmic koal but
i found the in former times - the command works when all the icons disapeared - i think -p means to 
restart with a new config)
sorry no more ideas - good luck
ciao
i forgot - i found on my box the file: /usr/share/doc/gdm/examples/custom.conf 
# GDM configuration storage
[xdmcp]
[chooser]
[security]
[debug]
---> but there is no manual page for it on the system. may be it's created by the commands above ?!

---

