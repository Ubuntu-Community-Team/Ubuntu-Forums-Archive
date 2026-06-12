---
title: "x11vnc unable to open xdisplay"
date: 2010-03-27
forum: General Help
---

### Post by wisie on 2010-03-27
Following this [guide]("https://help.ubuntu.com/community/VNC"), I wanted to setup VNC to remote connect to my ubuntu desktop. I installed x11vnc, openssh-server and also edited [gdm.conf]("https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login"). But I can't manage to get it to work..

Running command:
sudo x11vnc -safer -localhost -once -nopw -auth /var/lib/gdm/:0.Xauth -display :0

I receive:
*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

If anyone could shed some insight to get it going I'd be grateful :)

Thanks

---

### Post by krunge on 2010-03-27
Does /var/lib/gdm/:0.Xauth even exist?  Is GDM using it?  I don't recall ever seeing that filename, it was /var/gdm/:0.Xauth for a long time, but in recent GDM's they've changed it again, this time to a file with a random name.

Are you already logged into the X session with your user?  If so you don't need the sudo or the -auth ...

---

### Post by stinkeye on 2010-03-27
I used this simple to follow tutorial and it worked.
[**_[COLOR="DarkRed"]Connect to a remote Linux desktop with x11vnc and Gtk VNC[/COLOR]_**]("http://www.ghacks.net/2010/01/24/connect-to-a-remote-linux-desktop-with-x11vnc-and-gtk-vnc/")

---

### Post by wisie on 2010-03-27
Thanks for the replies :)


I must admit I'm a newbie to all of this but here goes.

I'm running 9.11 non server edition. The box practically runs under my cupboard so having access to VNC isn't a huge deal as I'm **slowly** starting to get the hang of terminal but it would be nice to get it going. 

> **krunge said:**
> Does /var/lib/gdm/:0.Xauth even exist?  Is GDM using it?  I don't recall ever seeing that filename, it was /var/gdm/:0.Xauth for a long time, but in recent GDM's they've changed it again, this time to a file with a random name.

Are you already logged into the X session with your user?  If so you don't need the sudo or the -auth ...

I don't think the user account is logged in as I just plugged the box into my monitor, tried connecting to it from my machine and it worked fine. But once I put it back underneath the cupboard without a monitor, keyboard and mouse plugged in I can't connect.

Any suggestions?

---

### Post by krunge on 2010-03-27
Sometimes the X server exits with fatal error if no monitor is attached.

Look at log files /var/log/Xorg.0.log and /var/log/Xorg.0.log.old to see if it is exiting because of this. (e.g. 'Fatal error, no screens found')

I believe there are some threads in these forums for an /etc/X11/xorg.conf Montior Section setting that let's you hardwire in monitor settings.

---

### Post by stinkeye on 2010-03-27
This thread has a solution: [_**[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1412565&highlight=monitor&page=2[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=1412565&highlight=monitor&page=2")

```
open the terminal and type
gksudo gedit /etc/default/grub

change the line 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **nomodeset**"

save file 
close
and then
sudo update-grub
```

---

### Post by wisie on 2010-03-27
Looks like that fixed the problem :)

Thanks everyone for your time and help!

---

### Post by asmoore82 on 2010-03-28
I would humbly recommend the link in my signature.

:popcorn:

---

