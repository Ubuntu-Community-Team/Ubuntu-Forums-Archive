---
title: "Gdm to start x server on display other than 0?"
date: 2011-07-15
forum: General Help
---

### Post by sakishrist on 2011-07-15
Hello,

I would like to know how I can make GDM to start the x server with another display number (and on different vt please). 

The reason for this is that I have a chroot environment and I believe I have installed the necessary packages but when I do **$ /etc/init.d/gdm start** it seems to start but no new x server is running on any of the vt.

Thanks!!!

---

### Post by sakishrist on 2011-07-15
Bump

Please help [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by sakishrist on 2011-07-15
Still no luck ...

I made the following changes to **/chroot/etc/gdm/custom.conf**:
```
[B][servers]
1=Standard[/B]

[daemon]
AutomaticLoginEnable=false
AutomaticLogin=sakishrist
TimedLoginEnable=false
TimedLogin=sakishrist
TimedLoginDelay=10
DefaultSession=gnome-classic
**FirstVT=10**
``` 
But nothing happened. When I type **service gdm start **I still get ```
gdm start/running, process 29711
``` or I get this error when I type **gdm start :1**:```
gdm start :1

** (gdm-binary:28104): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:28104): WARNING **: Could not acquire name; bailing out

``` (I have bound /var/run/dbus to /chroot/var/run/dbus)

Any help or ideas will be greatly appreciated! [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by sakishrist on 2011-07-16
I also tied with **startx -- :1 &** but nothing happened. 

Is this not possible? [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by sakishrist on 2011-08-03
Hello everyone,

I finally managed  to do this.

The first thing I did was to install the exact same graphics drivers on the chrooted environment. (My chroot is a 32bit one but I installed the 64bit drivers - the exact same as the host ones.) I am not sure if this step was necessary. 

Then I added localhost to the list of clients allowed to connect to the X server: ```
**xhost +localhost**
``` Afterwards I started an x server with: ```
**X :1 -ac**
``` And lastly I started the gnome session: ```
**gnome-session gnome-session --display=localhost:1**
```


The thing is that I still have some problems:

[LIST]
[*]The most serious one is that when I attempt to run gnome-terminal I get a weird error: > There was an error creating the child process for this terminal.

getpt failed: no such file or directory I also tried xterm but that one did not even give an error, nothing appeared on the screen at all. Other programs from the main menu seem to run fine.[/LIST]

[LIST]
[*]Another thing is that would like to be able to chose the virtual terminal that the X server starts on. For example, I would like the host to be on the default (7) and the chroot to be at the end (eg 11.) Anyway, this is more of an "aesthetic" issue.
[/LIST]
Thanks in advance.

---

### Post by WorMzy on 2011-08-03
Have you mount --bind'ed /dev, /dev/pts, /proc, and /sys onto the chroot?

---

### Post by sakishrist on 2011-08-03
> **WorMzy said:**
> Have you mount --bind'ed /dev, /dev/pts, /proc, and /sys onto the chroot?
I had forgotten /dev/pts. 

Thanks a million.

PS: /dev/pts is inside /dev , but why do I have to mount it separately? I also have to do it for the contents of my media folder, I can not just mount /media.

---

### Post by WorMzy on 2011-08-03
Because /dev/pts is a separate filesystem to /dev, and mount --bind doesn't mount submounts.

Try

```
mount --rbind /dev/ /chroot/dev
```
next time. I've never used it myself, but according to the man page, it *does* mount submounts.

---

### Post by sakishrist on 2011-08-04
Thanks!!!

---

