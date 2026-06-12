---
title: "Accessing firefox remotely"
date: 2011-12-05
forum: General Help
---

### Post by Kissell on 2011-12-05
I can ssh from one ubuntu box to another with the -X parameter, then launch firefox and it pulls up a remote instance of the firefox browser that gives me access to the files and internet connection of the remote server.

The problem is I want normal users to be able to do this from windows client machines without having to install any software.

Does anyone know if I install a web based ssh client on the server, such as shellinabox, will I be able to launch X11 programs through it?  It's clear I can get a command line shell, but will it work to launch GUI programs?

Or is there another way to accomplish this?  Preferrably I want users to login through a webpage and it pull up a firefox browser for them without them seeing a command line at all.

---

### Post by oldtimer7777 on 2011-12-05
TeamViewer 6 is what I use to do the exact same thing and a whole heck of a lot less complicated.

> **Kissell said:**
> I can ssh from one ubuntu box to another with the -X parameter, then launch firefox and it pulls up a remote instance of the firefox browser that gives me access to the files and internet connection of the remote server.

The problem is I want normal users to be able to do this from windows client machines without having to install any software.

Does anyone know if I install a web based ssh client on the server, such as shellinabox, will I be able to launch X11 programs through it?  It's clear I can get a command line shell, but will it work to launch GUI programs?

Or is there another way to accomplish this?  Preferrably I want users to login through a webpage and it pull up a firefox browser for them without them seeing a command line at all.

---

### Post by Kissell on 2011-12-05
Yeah, and ssh GUI commands won't work from a windows client because there is no X11 server...  

I was just trying to find a way to get them to use only the firefox app, not be burdened with a whole heavy remote desktop session that was unnecessary.  ssh remote control GUI apps works so much better/faster than remote desktop, much less bandwidth...  and so easy... if both computers are linux.  But I need to let windows clients too.

I'm not sure team viewer will work well for me.  I don't want to share the desktop, I want to allow potentially dozens of people to each have their own remote desktop session.  I guess I'll look into an RDP or VNC solution...  but I always run into problems fighting getting those working in Ubuntu.

---

### Post by oldtimer7777 on 2011-12-05
> **Kissell said:**
> Yeah, and ssh GUI commands won't work from a windows client because there is no X11 server...  

I was just trying to find a way to get them to use only the firefox app, not be burdened with a whole heavy remote desktop session that was unnecessary.  ssh remote control GUI apps works so much better/faster than remote desktop, much less bandwidth...  and so easy... if both computers are linux.  But I need to let windows clients too.

I'm not sure team viewer will work well for me.  I don't want to share the desktop, I want to allow potentially dozens of people to each have their own remote desktop session.  I guess I'll look into an RDP or VNC solution...  but I always run into problems fighting getting those working in Ubuntu.

Sounds like you need to provide a Citrix ICA-ish client for your users.  I don't know what the compatible software would be for Ubuntu, but Citrix does that role really well.

---

### Post by Kissell on 2011-12-05
I've read that "apt-get install xrdp" will do exactly what I want...  it should allow multiple users to login via the windows remote desktop connection application all at the same time and each get their own separate desktops.  But I can't get the darn thing to work...  when I login I just get a blank screen.

---

### Post by azmyth on 2011-12-05
You can use a combination of xrdp on linux side and remote desktop on the Windows side at least on 7.

What mode do you have set when you try to login? Also you can enable the log by editing the /etc/xrdp/sesman.ini assuming you're using one of the sesman modes.

---

### Post by Kissell on 2011-12-05
None of the modes worked...  This seems to be a common problem in v11.10.

I'm currently following this guide to rebuild x11rdp and xrdp from scratch using newer versions instead of what's in the repository.  Evidentally xrdp from the repository doesn't work with the x11rdp I was using...  maybe...  it's taking forever to recompile x11.

[http://scarygliders.net/2011/11/17/x11rdp-ubuntu-11-10-gnome-3-xrdp-customization-new-hotness/]("http://scarygliders.net/2011/11/17/x11rdp-ubuntu-11-10-gnome-3-xrdp-customization-new-hotness/")

---

### Post by Kissell on 2011-12-05
I found this bug report that describes what was happening everytime I've tried to use xrdp in Ubuntu 11.10.

[https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/900016]("https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/900016")

---

### Post by azmyth on 2011-12-05
Did you try using a different desktop something like fluxbox by adding this to the /home/username/.xsession file by just adding fluxbox on the top line.

---

### Post by Kissell on 2011-12-05
another display manager doesn't help.

I had it to a point after recompiling everything that I would get my wallpaper, but nothing else...  now I keep getting "login failed".  

/var/log/xrdp-sesman.log says:
> 
[20111205-21:56:22] [ERROR] X server -- no display in range is available

---

### Post by mbeccaria on 2013-01-11
> **Kissell said:**
> another display manager doesn't help.

I had it to a point after recompiling everything that I would get my wallpaper, but nothing else...  now I keep getting "login failed".  

/var/log/xrdp-sesman.log says:

I got exactly your problem. it looks like the system is running out of resources. were you able to solve it ?

---

### Post by mbeccaria on 2013-01-11
> **mbeccaria said:**
> I got exactly your problem. it looks like the system is running out of resources. were you able to solve it ?

FYI
I have solved increasing the parameter MaxSession from 10 to 100 into /etc/sesman.ini
Hope it can help

---

