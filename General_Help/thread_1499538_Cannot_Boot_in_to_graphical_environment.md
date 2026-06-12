---
title: "Cannot Boot in to graphical environment"
date: 2010-06-02
forum: General Help
---

### Post by subodh.rohilla on 2010-06-02
I am using 10.04. The grub is working properly but i can't login in graphical environment because the system stops at the ubuntu boot logo. 

However, TTY is working properly and i am able to login in all the tty [F1-F6]. I think the problem is with xserver but I don't know how to fix it. 
Plz help

---

### Post by Spr0k3t on 2010-06-02
I have no clue what your hardware is, so I'm going to stab in the dark on this one.  I used this to fix my laptop so it would boot.

[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

The laptop uses a Intel i815 chipset for graphics.  Have a look at that to see if the aplied knowledge fits your issue.  If you have a different graphics card, please post more information regarding your hardware.  If you could do "lspci -nn" and paste the output, that would help immensely to troubleshoot your issue.

---

### Post by BoneKracker on 2010-06-02
You might try looking at dmesg and your Xorg log file.

---

### Post by garvinrick4 on 2010-06-02
> **subodh.rohilla said:**
> I am using 10.04. The grub is working properly but i can't login in graphical environment because the system stops at the ubuntu boot logo. 

However, TTY is working properly and i am able to login in all the tty [F1-F6]. I think the problem is with xserver but I don't know how to fix it. 
Plz help Not a lot of info to work with but sounds like this.

Type in 

```
startx
```see if you get a desktop:

rick@rick-laptop:~$ aptitude show gdm
Package: gdm
State: installed
Automatically installed: no
Version: 2.30.2-0ubuntu1
Priority: optional
Section: gnome
Maintainer: Sebastien Bacher <seb128@ubuntu.com>
Uncompressed Size: 7,971k
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.29.3), libattr1 (>=
         2.4.41-1), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6
         (>= 2.4), libcairo2 (>= 1.2.4), libcanberra-gtk0 (>= 0.4), libcanberra0
         (>= 0.2), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78),
         libdevkit-power-gobject1 (>= 1:0.9.1), libfontconfig1 (>= 2.8.0),
         libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.27.0), libglib2.0-0 (>=
         2.23.5), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1),
         libgtk2.0-0 (>= 2.16.0), liborbit2 (>= 1:2.14.10), libpam0g (>=
         0.99.7.1), libpanel-applet2-0 (>= 2.26.0), libpango1.0-0 (>= 1.14.0),
         libpolkit-gobject-1-0 (>= 0.94), libpopt0 (>= 1.15), libselinux1 (>=
         1.32), libwrap0 (>= 7.6-4~), libx11-6 (>= 0), libxau6, libxdmcp6,
         libxklavier16 (>= 5.0), libxml2 (>= 2.6.27), zlib1g (>= 1:1.1.4),
         debconf (>= 0.5) | debconf-2.0, gconf2 (>= 2.10.1-2), upstart-job,
         adduser, libpam-modules (>= 0.72-1), libpam-runtime (>= 0.76-13.1),
         gnome-session-bin, kbd | console-tools, udev (>= 149-2)
Recommends: xserver-xorg, metacity | x-window-manager, gnome-settings-daemon |
            xfconf
Suggests: locales, uswsusp, libpam-gnome-keyring, gnome-power-manager,
          gnome-orca, gok, gnome-mag
Conflicts: fast-user-switch-applet, gdm-snapshot, libxklavier15 (<
           4.0-0ubuntu2), xsplash (< 0.8)
Breaks: usplash
Replaces: fast-user-switch-applet, gdm-snapshot
Provides: x-display-manager
Description: GNOME Display Manager
 gdm provides the equivalent of a "login:" prompt for X displays- it pops up a
 login window and starts an X session. 
 
 It provides all the functionality of xdm, including XDMCP support for managing
 remote displays. 
 
 The greeting window is written using the GNOME libraries and hence looks like a
 GNOME application- even to the extent of supporting themes! By default, the
 greeter is run as an unprivileged user for security.

If you have to:

```
sudo apt-get remove gdm
``````
sudo apt-get clean

``````
sudo apt-get install gdm
```

restart

---

### Post by subodh.rohilla on 2010-06-02
Thanks to all for helping.

When I tried out the commands , I found that the filesystem is corrupted.( Some error messages of duplicate inodes were there )
I gave fsck command from livecd and now my system is working properly.

---

