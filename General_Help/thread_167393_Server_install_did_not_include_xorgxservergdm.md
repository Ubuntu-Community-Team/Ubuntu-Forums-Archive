---
title: "Server install did not include xorg/xserver/gdm"
date: 2006-04-28
forum: General Help
---

### Post by nimy on 2006-04-28
Hi,

I installed ubuntu on a new drive when my old one started to fail, following the same instructions that had worked before, with the same 5.10 Install CD, working with [http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2)
After two attempts, I can confirm that this installation does not include the xserver, since no X11 directory was installed in /etc, although I don't recall any problems like this on my earlier install of ubuntu.
So I started installing these packages:
xorg-common
xfonts-base, xfonts-100dpi, xfonts-scalable packages
xserver-common
gdm
I must need more than what I have installed, because the Xserver fails to start with this error: cannot stat /etc/X11/X - no such file
Also, I have no xorg.conf file.
I wasn't sure what order these packages needed to be installed, but generally followed the sequence you see above and did not see any errors on install.
I have a nVidia GEForce2 MX 32MB card and probably need to get/install an nVidia package for it, but the absence of an xorg.conf file disturbs me.

---

### Post by tombeharrell on 2006-04-28
Umm, the server install means a non-graphical text-only server, such as a remote webserver you may have in a data centre. There is no X.org, Gnome, KDE etc.

You can use it as a minimal install then install ubuntu-desktop, kubuntu-desktop, or xubuntu-desktop to get clean versions of each environment.

sudo apt-get install ubuntu-desktop

Installing the correct desktop metapackage will install all the relevant graphical systems and default application set.

---

### Post by nimy on 2006-04-28
I also installed gnome, which I had missed, however the Xserver startup error is the same, and there is still no xorg.conf file in /etc/X11

---

### Post by tombeharrell on 2006-04-28
Try:
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by engla on 2006-04-28
There is no problem -- gdm, Xorg, gnome etc are not supposed to be in a server install.

What are you going to use your computer for? -- this is what you have to start from. It it's for desktop/surfing/etc, you should do a normal install, not a server install.

---

### Post by nimy on 2006-04-28
Thanks very much - just looking for a GUI interface on a server setup...tried all this in a hurry, got an xserver error disabling gdm and showing lots of OS kernel info but no specific error message...will work on this later when I get backl

---

### Post by nimy on 2006-04-29
My card didn't like frame buffering, but once I disabled that, all was ok...

Other things I did: checked the resolution (1280x1024, according to another user in this forum) and the excellent discussion on nvidia drivers from tseliot (not the poet, but the dapper drake tester in Italy) - I installed the nvidia driver (method 1) because  at that point gdm would not start.

Thanks to all :)

---

### Post by nudaz on 2006-06-29
[QUOTE=tombeharrell]sudo apt-get install ubuntu-desktop[/QUOTE]

Thanks - I was looking all over for that

> Installing the correct desktop metapackage will install all the relevant graphical systems and default application set.

How is a n00b to know the correct desktop metapackage?

I'm using the server to run VMware server, ran into problems regarding libX**.so.6 not found etc

thanks again

---

