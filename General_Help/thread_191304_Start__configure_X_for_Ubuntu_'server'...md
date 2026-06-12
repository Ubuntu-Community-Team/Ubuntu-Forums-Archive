---
title: "Start / configure X for Ubuntu 'server'.."
date: 2006-06-07
forum: General Help
---

### Post by cowmix on 2006-06-07
I just installed Ubuntu server.. and its great so far..

The problem is that I am so spoiled by modern Linux distros that I forgot how to configure and start X windows from the command line w/o going through an installer (like with Ubuntu 'desktop'.)

Is there a mini-HowTo the goes through how you get X working with Ubuntu server? If there is, I can't seem to find it.

thanks!

---

### Post by DarthMandeep on 2006-06-07
All you need to do is install the xorg server and your choice of window manager or desktop environment. Then you can start the GUI with the startx command. If you want to setup the server to boot to the GUI automatically install GDM.

---

### Post by cowmix on 2006-06-07
I installed XFCE4 and xfonts-base.. and here is where I am at..


```
admin@dapper-host:/usr/X11R6$ startx
xauth:  creating new authority file /home/admin/.serverauth.4181

XFree86 Version 3.3.6 / X Window System
(protocol Version 11, revision 0, vendor release 6300)
Release Date: January 8 1999
        If the server is older than 6-12 months, or if your card is newer
        than the above date, look for a newer version before reporting
        problems.  (see http://www.XFree86.Org/FAQ)
Operating System: Linux 2.2.17 i686 [ELF] 
Configured drivers:
  VMware: server for VMware graphics adapters (Patchlevel 0)
(using VT number 7)

XF86Config: /etc/XF86Config
(**) stands for supplied, (--) stands for probed/default values
(**) Mouse: type: ps/2, device: /dev/mouse, buttons: 3
(**) VMware: Graphics device ID: "VMware SVGA"
(**) VMware: Monitor ID: "vmware"
Warning: The directory "/usr/X11R6/lib/X11/fonts/misc/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/Type1/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/Speedo/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/75dpi/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/100dpi/" does not exist.
         Entry deleted from font path.
Warning: FontPath is completely invalid.  Using compiled-in default.
Warning: The directory "/usr/X11R6/lib/X11/fonts/misc/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/Speedo/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/Type1/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/75dpi/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/100dpi/" does not exist.
         Entry deleted from font path.

Fatal server error:
No valid FontPath could be found



When reporting a problem related to a server crash, please send
the full server output, not just the last messages


XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
Couldnt get a file descriptor referring to the console



```

---

### Post by DarthMandeep on 2006-06-08
Fonts issues are always annoying. Make sure you've got the other required fonts. I believe xfonts-scalable and one of the xfonts-*dpi packages are needed.

---

### Post by cowmix on 2006-06-08
Arg.. no dice.. still the same error.

[QUOTE=DarthMandeep]Fonts issues are always annoying. Make sure you've got the other required fonts. I believe xfonts-scalable and one of the xfonts-*dpi packages are needed.[/QUOTE]

---

### Post by Face1 on 2006-06-08
You could always install the xubuntu-desktop package.  This would install everything you would get with a xubuntu installation that you do not already have.

---

### Post by cowmix on 2006-06-08
Yeah.. I thought about that.. but I wanted my VMWare image I am making as light-weight as possible.. the default server image is very lite.... 

... and then I wanted to add the minium for XFCE...

---

### Post by Face1 on 2006-06-09
I see...Well you could install xubuntu-desktop, and then take out all the non-essential bits...but that would be a bit tedious.

---

### Post by cowmix on 2006-06-09
Arg.. no dice..

I did that.. and I still get the same error..

I am going to start over I think.

[QUOTE=Face1]I see...Well you could install xubuntu-desktop, and then take out all the non-essential bits...but that would be a bit tedious.[/QUOTE]

---

### Post by Zed on 2006-06-09
If you want XFCE, then, yeah, install xubuntu-desktop.

[Ubuntu Lite](http://www.ubuntulite.org/dokuwiki/doku.php?id=manual_installation) gives an example of what you have to install on top of ubuntu-server to get a lightweight system.

Here's one example of getting from ubuntu-server to a window manager-capable system:

```

sudo aptitude install x-window-system-core
sudo aptitude install ratpoison # or your lightweight window manager of choice
echo 'exec ratpoison'|cat > ~/.xinitrc
startx

```

This is not minimal -- x-window-system-core includes a lot of standard X utilities, many of which you could get by without. But it's a lot slimmer than you'll get with any of the desktop metapackages.

With just this, the system will start in a console, and you'll login that way, and you'll have to enter startx if you want X. If you prefer to start in X by default, then:

```

sudo aptitude install xdm # or maybe wdm, by preference
echo 'exec ratpoison'|cat > ~/.xsession

```

---

### Post by cowmix on 2006-06-12
Ok.. you instructions in this post completely helped out. .

thanks!

[QUOTE=Zed]If you want XFCE, then, yeah, install xubuntu-desktop.

[Ubuntu Lite](http://www.ubuntulite.org/dokuwiki/doku.php?id=manual_installation) gives an example of what you have to install on top of ubuntu-server to get a lightweight system.

Here's one example of getting from ubuntu-server to a window manager-capable system:

```

sudo aptitude install x-window-system-core
sudo aptitude install ratpoison # or your lightweight window manager of choice
echo 'exec ratpoison'|cat > ~/.xinitrc
startx

```

This is not minimal -- x-window-system-core includes a lot of standard X utilities, many of which you could get by without. But it's a lot slimmer than you'll get with any of the desktop metapackages.

With just this, the system will start in a console, and you'll login that way, and you'll have to enter startx if you want X. If you prefer to start in X by default, then:

```

sudo aptitude install xdm # or maybe wdm, by preference
echo 'exec ratpoison'|cat > ~/.xsession

```[/QUOTE]

---

