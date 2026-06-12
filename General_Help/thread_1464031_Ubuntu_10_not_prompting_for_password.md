---
title: "Ubuntu 10 not prompting for password"
date: 2010-04-27
forum: General Help
---

### Post by ZeroMinuS on 2010-04-27
OS: Ubuntu 10.04 B2
System: MacBook Pro (1st gen)

When I am running a program that requires an administrative password such as update-manager, it will not prompt for a password. Instead you see a "Starting Administration" load on the bottom taskbar. A few seconds later it disappears resulting in the application freezing until I kill the process. 

If use sudo in the terminal to run the application, it will run properly. For example, using apt-get is the only way I can updates to install.

From what I can tell, it appears the problem is the prompt for password keeps crashing. I had no problems until I ran updates for the first time after the initial installation. Is there a way to fix this?

---

### Post by HGI on 2010-11-16
> **ZeroMinuS said:**
> OS: Ubuntu 10.04 B2
System: MacBook Pro (1st gen)

When I am running a program that requires an administrative password such as update-manager, it will not prompt for a password. Instead you see a "Starting Administration" load on the bottom taskbar. A few seconds later it disappears resulting in the application freezing until I kill the process. 

If use sudo in the terminal to run the application, it will run properly. For example, using apt-get is the only way I can updates to install.

From what I can tell, it appears the problem is the prompt for password keeps crashing. I had no problems until I ran updates for the first time after the initial installation. Is there a way to fix this?

Hello Colleagues,
I have the described situation (Ubuntu 10.4 Kernel 2.6.32-25-generic GNOME 2.30.2), too. Until now I went around the problem with repeated start of programmes waiting for administrative password: the second run didn't stop before prompt for password. This method is impossible in case of embedded start (e.g. share directories from nautilus). Has somebody a solution?
Thank you. HGI

---

### Post by ArcherB on 2011-02-24
I have the same problem with Update Manager.  It will check for updates without problem and let me know when updates are available.  When I click "Install Updates", the button stays depressed for a second and nothing happens.  If I run "gksu update-manager" the system asks for a password and runs normally (works fine).  If I run sudo apt-get upgrade, it runs fine as well.

It appears that the update-manager application is simply not asking for the password and gives up waiting for it.

***UPDATE***
If I click "Settings" it asks for the password and allows me to change whatever sources I like.  After clicking OK, and clicking the update button, same as before... nothing.

---

