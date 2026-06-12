---
title: "Uninstall Firefox Pre w/ Synaptic, Ubuntu won't boot"
date: 2010-03-15
forum: General Help
---

### Post by RonB123123 on 2010-03-15
I uninstalled Firefox 3.6 pre with Synaptic, Ubuntu now will not boot. I tried booting into recovery mode and selected fix broken packages, at first it said 30 packages selected but it would download and would not install them. I tried rebooting and going into recovery again and this time it said 0 selected but still asked me to install, when I hit y, it says at the end 0 out of 0 installed. However it is possible to login using the recovery mode. 

I tried booting up regularly and the ubuntu logo comes up but fails when trying to show the login screen. It shows a black screen with 2 very small horizontal white dashes at the top of the screen. I am now booting off a live CD mounted on a USB in order to fix this problem.

What can I do or install to fix this? 

Thanks,
Ron

---

### Post by dadrc on 2010-03-15
With uninstalling Firefox you probably uninstalled XulRunner, too, since 3.6 uses another version of XulRunner than 3.5.

Obviously, without error messages, this is just a guess, but try booting into recovery mode, disable whatever repository you added to get Firefox 3.6 and reinstall Firefox 3.5, which should also install XulRunner and hopefully fix your problem.

---

### Post by RonB123123 on 2010-03-15
Hi. I tried booting in recov mode again and tried to reconfigure the x server using:

dpkg-reconfigure -phigh xserver-xorg

and that worked so I tried to start the x server using:

startx

and that failed. I'm wondering if the x server is damaged and that's why I'm not seeing a GUI. What packages should I reinstall to fix the x server or what should I do to so I can at least boot into Ubuntu 9.10??

---

### Post by RonB123123 on 2010-03-15
hi dadrc,

I was able to rollback my firefox 3.6 to 3.5 by rebuilding all my repositories using lynx. I reinstalled xulrunner-1.9.1 and the same problem occurs when I try to boot up normally.

For some reason the x server or xorg or gnome-session or gdm-gnome-session is messed up. I tried reinstalling as much as I could, but to no avail. Is there anything I can do, such as turn on debug mode or something to narrow down the problem?

Is there a quick fix for it or a way to rollback or anything I can do? Cause I'd rather not reinstall the OS when I have made many changes to it.

Thank you,
Ron

---

### Post by RonB123123 on 2010-03-15
any help please?

---

### Post by prodigy_ on 2010-03-15
> **RonB123123 said:**
> any help please?
```
sudo apt-get remove gdm ubuntu-desktop
sudo apt-get autoremove
sudo apt-get install gdm ubuntu-desktop
```
It'll take long but may work if your X/Gnome config is ok.

---

### Post by RonB123123 on 2010-03-15
Thank you for the response, I tried reinstalling gdm and ubuntu-desktop several times and the same thing happens. It's hard to imagine that the entire system can break down by uninstalling a program that shouldn't have affected the core of the entire operating system.

Anyway...
Is there a way to get detailed information on the error(s) so I can pinpoint exactly what's failing to figure out what missing/broken packages need to be installed for it to start working? or is it not that simple?

---

### Post by sandyd on 2010-03-15
> **RonB123123 said:**
> Thank you for the response, I tried reinstalling gdm and ubuntu-desktop several times and the same thing happens. It's hard to imagine that the entire system can break down by uninstalling a program that shouldn't have affected the core of the entire operating system.

Anyway...
Is there a way to get detailed information on the error(s) so I can pinpoint exactly what's failing to figure out what missing/broken packages need to be installed for it to start working? or is it not that simple?
can you post the contents of /var/log/syslog ?

boot from a livecd to do that.

---

### Post by RonB123123 on 2010-03-17
Im on a live CD now and just copied the syslog over:

[http://www.pastebin.com/sWEU4YX9](http://www.pastebin.com/sWEU4YX9)

~Ron

---

### Post by RonB123123 on 2010-03-18
.

---

### Post by RonB123123 on 2010-03-18
.

---

### Post by RonB123123 on 2010-03-21
Thank you for absolutely no help on this. I've copied my home directory and my /var/www directory and am going to reinstall the system. I would have rather just fixed the problem but as I had no idea on how to fix even after looking at the logs and googling and fixing as many errors I could find, this seemed to be the best option.

What I learned from this mess: If you want a new version to a program (i.e. upgrade from FF 3.5 to 3.6) use **aptitude** or **apt-get** not [s]synaptic[/s]. And also if anything goes wrong on your system to make it inoperable, then use the Ext2 Volume Manager on your Windows partition to read a Ext2, Ext3, or Ext4 drive and copy over the important directories. 

Then use partitioning software, preferably the GUI version of gparted to delete the linux partition, allocate the new free space to the Windows HD (if you want), and install Linux once again. 

Maybe a new flavor this time. 

~Ron

PS: Fixed by reinstalling and saving all data to Windows partition. Here's how I did it.
[http://ubuntuforums.org/showthread.php?p=9016787](http://ubuntuforums.org/showthread.php?p=9016787)

---

