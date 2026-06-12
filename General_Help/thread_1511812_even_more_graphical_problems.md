---
title: "even more graphical problems"
date: 2010-06-17
forum: General Help
---

### Post by surrealillusions on 2010-06-17
Hi all,

I've been trying for 3 days now to sort out these ati driver issues, and today its even worse than what it was.

I've tried everything from the closed source drivers to open source. All steps associated with installing them either didnt work or part of it didnt exist.

Now, I've got a system thats even slower. Moving windows and even scrolling in the browser is more jumpy than a kangeroo trampoline club.

This is driving me insane, I cant do any work, especially now its this slow. Why the hell did i upgrade to 10.04....arrgh!!

How the heck do i get it back to what it was, even with no effects was better than this.

Installing the ATI drivers from their website doesn't work.

---

### Post by beckols on 2010-06-17
What are your system specs?  And could you go into a little more detail about what you've already tried?

---

### Post by surrealillusions on 2010-06-17
Running Ubuntu 10.04, ATI Radeon HD series graphics card.

Tried downloading the ATI drivers from their site (both 10-5 and 10-6 versions).

Tried the sudo sh ./ati-driver-installer.run --buildpkg Ubuntu/lucid in terminal, but that comes up with errors. I've currently got broken packages, but yet they dont appear in the package manager.

Tried purging all fglrx and xorg stuff, and ATI stuff, then installing them - nothing.
Tried open source drivers, but never really understood the steps so that didnt work.

Just at wits end really in what to do, what to search for.

---

### Post by beckols on 2010-06-17
Do you know, by chance, the exact model of video card you have?

---

### Post by surrealillusions on 2010-06-17
HD4350 is the model of graphics card.

Have sorted out the jumpy windows and FF scrolling by restoring an xorg.config file that was renamed - someone i know kinda knows somethings about linux and asked me to do that while trying to solve the problem of no visual effects.

Still would like to have the visual effects enabled though.

---

### Post by beckols on 2010-06-17
Could you post your xorg.conf file as well as the output from 'glxinfo'?

---

### Post by surrealillusions on 2010-06-17
xorg.conf is empty

and results of glxinfo in terminal:

name of display:  :0.0
X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 153 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 14
Current serial number in output stream: 14

---

### Post by beckols on 2010-06-17
Could you post the output of:
```

X -version
dpkg -l | grep fglrx

```
Also is this an upgrade or a clean install?

What exactly happened when you tried using the proprietary driver?

---

### Post by surrealillusions on 2010-06-17
Upgrade from 9.10 to 10.04

When I updated, I got 3 broken packages to do with the fglrx, and the visual effects didnt work. 3D acceleration also doesn't work when running VMware.

Output of X version:

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux nick-desktop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=02790633-eb36-4a2a-9e57-6e0b8fbd927a ro quiet splash
Build Date: 09 June 2010  10:55:28AM
xorg-server 2:1.7.6-2ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
```

And the dpkg -l | grep fglrx

```

ii  fglrx                                 2:8.723.1-0ubuntu4                              Video driver for the ATI graphics accelerators

```

---

### Post by XSAlliN on 2010-06-17
Upgrade to a major distribution is never safe.

> **surrealillusions said:**
> HD4350 is the model of graphics card.

Have sorted out the jumpy windows and FF scrolling by restoring an xorg.config file that was renamed - someone i know kinda knows somethings about linux and asked me to do that while trying to solve the problem of no visual effects.

Still would like to have the visual effects enabled though.

Don't bother with Proprietary Drivers (as in FGLRX), those are junk for general use... they're just for specific purposes like gaming (as if that was meant for Linux distributions) and graphic workstations, which are not Ubuntu related.

I have an HD 4850 and Open Source drivers run just fine for general use.

Try this:

> sudo apt-get install --reinstall xserver-xorg-video-ati 

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

sudo gedit /etc/X11/xorg.conf (remove all content, leave it empty)

...also check in Synaptic and see if "**xserver-xorg-video-fbdev**" is installed.

=====

But before that, completely remove FGLRX

> sudo sh /usr/share/ati/fglrx-uninstall.sh

sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev

You'll have to delete xorg.conf backup files for FGLRX.

---

### Post by surrealillusions on 2010-06-17
> 
sudo sh /usr/share/ati/fglrx-uninstall.sh


Doesn't work, get this in terminal:

sh: Can't open /usr/share/ati/fglrx-uninstall.sh

and xserver-xorg-video-fbdev is installed.

to delete xorg.conf backup files for FGLRX, will I have to do that manually thru terminal or will it do it when running the 2nd line after the above one (which failed).

:)

---

### Post by surrealillusions on 2010-06-17
That took some doing.

[https://wiki.ubuntu.com/X/RadeonXpress](https://wiki.ubuntu.com/X/RadeonXpress) - from that site, scroll down to 'desktop effects'

The stuff that it tells you to put in the xorg.conf file really screws up the system. It wont boot up. Had to boot up from the installation CD, go through the test run, and edit the xorg.conf file on the main hard drive via terminal in the test run, which took alot of trial and error in finding it, editing it etc..

The line below to add

SKIP_CHECKS="yes"

to .config/compiz/compiz-manager

is all I needed, along with XSAlliN's instructions on the previous page of this thread.

All that trouble just to get effects going...I need a holiday now...

Thanks for help guys. :)

[FONT=monospace][B][FONT=Verdana][/FONT]
[/B][/FONT]

---

