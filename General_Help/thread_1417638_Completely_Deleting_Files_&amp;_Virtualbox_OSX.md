---
title: "Completely Deleting Files &amp; Virtualbox OSX"
date: 2010-02-27
forum: General Help
---

### Post by giddyup306 on 2010-02-27
Hello everyone!  This is my first post on here so I apologize if this is in the wrong forum.  

It turns out I caught the Linux bug.  I'm now completely obsessed with it.  Most of the time if I can't get something to work I do a quick web search, and I find the solution to my problem in the first link or three.  This is the exception.  I wanted to install XP or 2000 using Virtualbox OSE just in case I needed to look up something on Windows or print something off (can't find any drivers for my  Lexmark printer).  I tried XP first and it gave me an error.  Then I tried 2000.  At this point I went to delete the program and try again.  The first thing I tried was *sudo apt-get remove virtualbox.  *Then when I re-installed it, I still had my settings and partitions on there.  I then went to the add/remove programs.  Same thing after the third install.  I then went to the Synaptic Package Manager and clicked completely delete files (or however it was worded).  After the install it still did the same thing as the previous times.  When I try and load Virtualbox it says "FATAL: No bootable medium found! System halted.".  Also sometimes my pointer will get locked inside Windows.  How do I get out of that?  The only thing I was able to find was hit CTRL + ALT + Back and it exits both Windows and Linux.  

Thanks in advance. 

Mike

---

### Post by Steven_B on 2010-02-27
Most (if not all) of the configuration files for VirtualBox are in your home directory, under .VirtualBox.  This directory is (intentionally) not removed when you remove the VirtualBox package, so delete it if you're trying to remove all old configurations.
Start with that, and then try a fresh install of Windows in VirtualBox.  Post back with any errors you get.

You should be able to hit the right control key to "uncapture" your mouse from VirtualBox.

---

### Post by mkvnmtr on 2010-02-27
I delete my virtual hard drives and machines through the Virtual Box program. There is more than one way but I believe you can get it done by right clicking on each and choosing delete.

---

### Post by giddyup306 on 2010-02-27
Okay I completely deleted the .virtualbox file and started from scratch.  Now after I've installed 2000 it gives me the error message *Please insert the Compact Disc labeled "Service Pack 4 CD" into your CD-ROM drive (D:) and then click OK.  *I do all this and it just wants to go through the setup again.  What am I doing wrong?

---

### Post by giddyup306 on 2010-02-27
After much kicking and screaming I finally got Win2k to work.  Now it won't recognize my flash drive or my CD-ROM drive, and can't access the net.  I have SP4 so it should support USB 2.0.  I found one site that had me modify the user group settings for the USB.  Another site said that the OSE version won't support USB.  It does recognize my USB mouse and keyboard tho...

---

### Post by giddyup306 on 2010-02-28
ttt

---

### Post by bpalone on 2010-02-28
As far as I know, the OPEN Source version does not support USB.  I would suggest removing the open source version and getting the PUEL version from here: [http://www.virtualbox.org/]("http://www.virtualbox.org/")

Once you have it installed, install guest additions and you should be good to go.  You may be able to use your Win2K virtual disk, so won't have to reinstall.

Download the manual while you are at Sun's website.  There is a lot of good info in it.

---

### Post by giddyup306 on 2010-02-28
I'm having a little bit of problems installing the non-OSE version.  I tried installing it with the .gdebi package installer, but after it's installed there is no virtualbox listing anywhere in applications.  I then used [http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu) to start the install again after deleting.  After the part where it says to download the package I tried running [I]cd /tmp
wget [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb)[/I] and it told me 

[I]root@ubuntu:/tmp# dpkg -i VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
dpkg: error processing VirtualBox_1.3.8_Ubuntu_edgy_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
root@ubuntu:/tmp# cd /tmp
root@ubuntu:/tmp# wget [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb)
--2010-02-28 18:38:15--  [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb)
Resolving [www.virtualbox.org]("http://www.virtualbox.org")... 88.198.19.108
Connecting to [www.virtualbox.org|88.198.19.108|:80]("http://www.virtualbox.org%7C88.198.19.108%7C:80")... connected.
HTTP request sent, awaiting response... 403 Forbidden
2010-02-28 18:38:15 ERROR 403: Forbidden.

root@ubuntu:/tmp# cd /tmp
root@ubuntu:/tmp# wget [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb)[/I]


I'm not sure if it makes a difference, but I have the .deb package on my desktop.

If I go to the last command it tells me:

VirtualBox_1.3.8_Ubuntu_edgy_i386.deb: No such file or directory
No URLs found in VirtualBox_1.3.8_Ubuntu_edgy_i386.deb.
root@ubuntu:/tmp# dpkg -i VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
dpkg: error processing VirtualBox_1.3.8_Ubuntu_edgy_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
root@ubuntu:/tmp#

---

### Post by bpalone on 2010-03-01
Is there a reason you downloaded such an old version?  They are up to something like version 3.x.x, The oldest I have used is 1.6.2 and I am still using Hardy 8.04.

I would recommend getting at least the Ubuntu version of 1.6.6.  I also recommend getting the manual, as it gives some good information on installing.  

You don't happen to be located in a country that Sun can't allow to have it are you?  If so, then I don't know what to tell you.

---

