---
title: "Issue when typing startx"
date: 2010-08-03
forum: General Help
---

### Post by Gamutech on 2010-08-03
Hello,

I just recently purchased a vps then typed apt-get install x-window-system-core xserver-xorg gnome-desktop-environment


Then I typed startx and this is what I get:


```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux gamerayslum.com 2.6.18-128.2.1.el5.028stab064.4 #1 SMP Mon Jul 27 12:45:01 MSD 2009 i686
Kernel command line: quiet
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug  3 18:47:19 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"

Fatal server error:
xf86OpenConsole: Cannot open /dev/tty0 (No such file or directory)


Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
xinit:  Server error.

```

I'm a fairly newb to linux, but I appreciate the help incredibly. It's probably something i'm stupidly doing

---

### Post by Gamutech on 2010-08-03
Anyone know? this is killing me right now ;(

---

### Post by jerenept on 2010-08-03
Why not use GDM? It shows a graphical login screen and comes with ubuntu standard.
startx seems a bit dated to me.

Just out of curiosity; is this a standard install of Ubuntu, or something else?

---

### Post by Gamutech on 2010-08-03
How do I use GDM?

And this is on my VPS standard installation, I believe. unless otherwise..i'm using a vps control panel at burst.net to do the installation.

How do I use GDM?

---

### Post by jerenept on 2010-08-03
Did the computer come with a GUI or did you install one?

GDM is the [GNOME Display Manager]("http://en.wikipedia.org/wiki/GNOME_Display_Manager").

EDIT: I was not aware of what a VPS was. I can try my best to help you, though.

---

### Post by Gamutech on 2010-08-03
I had to install it. I wish it came with one. I installed ubuntu 9.10 for x64.

I have no idea how to start GDM, I doubt it's even installed. 

So from the command line I installed gnome, and then when doing startx this error came up.

Didn't touch the server other than that.

---

### Post by Smart Viking on 2010-08-03
> **Gamutech said:**
> I had to install it. I wish it came with one. I installed ubuntu 9.10 for x64.

I have no idea how to start GDM, I doubt it's even installed. 

So from the command line I installed gnome, and then when doing startx this error came up.

Didn't touch the server other than that.

This is the best way to install gnome in ubuntu, try that and see if it works after that:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by linux18 on 2010-08-03
```
 xinit 
```

---

### Post by jerenept on 2010-08-03
it is really recommended to install "ubuntu-desktop" as it installs a complete ubuntu desktop environment.

```
sudo aptitude install ubuntu-desktop
```
(You might want to remove Gnome first)

---

