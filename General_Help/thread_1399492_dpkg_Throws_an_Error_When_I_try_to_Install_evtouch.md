---
title: "dpkg Throws an Error When I try to Install evtouch"
date: 2010-02-05
forum: General Help
---

### Post by fiddler616 on 2010-02-05
Hello,

I just got a secondhand HP Pavilion tx1000 tablet. I'm trying to make sure that everything is working OK while I wait for my hard drive to come in the mail, and Googling showed that I need the package [FONT="Courier New"]xserver-xorg-input-evtouch[/FONT] to make the touchscreen work. However, I can't install it. Here's what the terminal says:

```
ubuntu@ubuntu:~$ aptitude search evtouch
p   xserver-xorg-input-evtouch      - Touchscreen-Driver for X.Org/XFree86 serve
ubuntu@ubuntu:~$ sudo aptitude install xserver-xorg-input-evtouch 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  xserver-xorg-input-evtouch 
0 packages upgraded, 1 newly installed, 0 to remove and 216 not upgraded.
Need to get 36.4kB of archives. After unpacking 250kB will be used.
Writing extended state information... Done
Get:1 http://archive.ubuntu.com karmic-updates/universe xserver-xorg-input-evtouch 0.8.8-0ubuntu6.1 [36.4kB]
Fetched 36.4kB in 0s (39.2kB/s)                 
Selecting previously deselected package xserver-xorg-input-evtouch.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `kpartx': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

How do I fix that?

This is Karmic AMD64, if that matters...

Thanks in advance

---

### Post by drs305 on 2010-02-05
> (Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `kpartx': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


If it's a simple problem with the lists referred to by dpkg, try this:
Open Synaptic. Settings, Repositories, Ubuntu Software tab. Untick all selected repositories in Synaptic (or Software Sources), then reselect them and Reload. This should redownload the applicable lists (kpartx is in *main)* and may solve the problem.

---

### Post by fiddler616 on 2010-02-06
Thanks.

What actually happened is I started booting off a USB drive instead of a CD (so I could save data between reboots), and evtouch installed successfully right off the bat. I guess I can't complain.

---

