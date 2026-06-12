---
title: "Startup Applications."
date: 2010-03-06
forum: General Help
---

### Post by Mickeyj4j on 2010-03-06
Hi i have some questions about ubuntu Sstartup Applications. 
there are some that i cant work out what they exactly do or/and if they are even needed.

Here are my computer specs. its a desktop. 

CPU:       Single core Intel Pentium 4 (UP) cache 512 KB flags (sse2) clocked at 1836.497 MHz 
System:    Host meowbuntu-desktop Kernel 2.6.31-20-generic i686 (32 bit) Distro Ubuntu 9.10 karmic

is it ok to disable these processes from startup applications. 

01 AT SPI Registry Wrapper 

02 Check for new hardware drivers - I don't think its needed. 

03 Disk Notifications - Are these really important to have. 

04 GNOME Keyring Daemon - I think this is system dependent 

05 GNOME Settings Daemon - I think this is system dependent

06 GNOME Settings Daemon Helper - I think this is system dependent  

07 Indicator applet - this is handy but is it necessary. 

08 Network Manager - i am not on a network. is this needed for my dsl broadband modem. 

09 PolicyKit Authentication Agent - i assume this is for security (if so i will leave) 

10 Power Manager - i assume this is more for laptops.

---

### Post by ibuclaw on 2010-03-06
I'd probably **uncheck** #2 in that list, but leave the rest alone.

Is there any reason why you wish to disable?

Slow boot? or slow login? other?

---

### Post by gnomefreak on 2010-03-06
I only have the following enabled:

1. Certificate and Key Storage  (this is new it seems, I don't recall this being in there before.)

2. Gnome Log In Sound

3. Gnome Settings Daemon

4. Personal File Sharing (New as well I think)

5. Power Manger 

6. PulseAudio Sound System

7. Secret Storage Service

8. SSH Key Agent

I don't recall some of these until today so they might have been enabled due to updates/new packages.
This is on Lucid at this time. 
Before some of these the only ones i had enabled were:
2 3 6 8

Number 3 enables your theme. IIRC when not loaded on start up it showed basic theme (like you get running in safe-mode)

---

### Post by gnomefreak on 2010-03-06
I have a problem with slow everything that is related to Kernel.
It is caused by hardware profiling, it is done purposely i have heard. If I restart after first boot it speeds it up to normal. I had opened a bug on it.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512410](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512410)

Maybe that is what you are seeing?

---

### Post by Mickeyj4j on 2010-03-06
> **gnomefreak said:**
> 
Before some of these the only ones i had enabled were:
2 3 6 8


what about 4 5 from my list they are gnome processes

---

### Post by gnomefreak on 2010-03-06
04 GNOME Keyring Daemon - This is not needed to load on start up. Here is more info on what it is and does.

05 GNOME Settings Daemon - I have this enabled. It does a few things that i will list below.

06 GNOME Settings Daemon Helper - I don't have this in start-up apps dialogue

Info about #5 below:

gnomefreak@Development:~$ show gnome-settings-daemon
Package: gnome-settings-daemon
Priority: extra
<snip>
Description: daemon handling the GNOME session settings
 This package contains the daemon which is responsible for setting the
 various parameters of a GNOME session and the applications that run
 under it. It handles the following kinds of settings:
 .
  * Keyboard: layout, accessibility options, shortcuts, media keys
  * Clipboard management
  * Theming: background, icons, GTK+ applications
  * Cleanup of unused files
  * Mouse: cursors, speed, accessibility options
  * Startup of other daemons: screensaver, sound daemon
  * Typing break
 .
 It also sets various application settings through X resources and
 freedesktop.org XSETTINGS.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 3y
Task: ubuntu-desktop, edubuntu-desktop, xubuntu-desktop, ubuntu-netbook

---

