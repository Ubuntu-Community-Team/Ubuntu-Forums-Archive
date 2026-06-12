---
title: "Shutdown or restart requires hard reset"
date: 2011-04-30
forum: General Help
---

### Post by gizmobay on 2011-04-30
I'm having the same issue as in this thread. The thread is locked so I'm starting a new one.

[http://ubuntuforums.org/showthread.php?t=1690434](http://ubuntuforums.org/showthread.php?t=1690434)

Basically, when I do a reboot or shutdown and then the system tries to start I get a blank screen thus I have to hit the reset button and then I'm showed a grub menu (not sure why I have it set to autoboot) and then I can boot properly.

The other people said solved but it's not solved for me. :confused:

---

### Post by gizmobay on 2011-05-02
bump

---

### Post by gizmobay on 2011-05-07
bump

---

### Post by gizmobay on 2011-05-18
bump

---

### Post by fidamehran on 2011-05-25
Buddy, we're in the same boat. But I can't solve it. No clear indication anywhere about what to do...

---

### Post by gordintoronto on 2011-05-25
It might help if you described your computer. Motherboard, CPU, memory, version of Ubuntu, type of installation (WUBI, dual boot, only Ubuntu).

The screen goes blank exactly when you would expect the BIOS display?

---

### Post by gizmobay on 2011-05-25
I'm running 11.04 64 bit with an intel i5 and I'm using a GeForce 7300 Desktop PC with a MSI motherboard. I'm using the nouveau drivers since the nvidia's do not work for me. The current nvidia's wouldn't boot into the desktop and the 173 left a line on the desktop. When I had the nvidia's installed for testing, it displayed the same behavior on reboot or shutdown

What happens is if I do a shutdown or reboot. The computer shutdown and then it restarts and then it shows the BIOS screen. After the BIOS screen flashes off I'm taken to a blank purpleish hue screen. I must then hit the hard reset button and then it sequences through the BIOS screen then I'm taken to the grub menu and then I select and then it starts as normal. Not sure why the grub menu displays as I have it set to start.

Since my original post, I saw the upgrade left previous versions of the kernel from 10.10. I thought this was my problem so I uninstalled the old kernels and reran grub-update but this didn't solve the problem. I've installed straight to the hard drive by using the internet to upgrade from 10.10 to 11.04. It's not a multi-boot system as this is the only OS I have.

---

### Post by gordintoronto on 2011-05-25
Very interesting! The shutdown seems to work fine, it's the start-up which fails the first time? Your sentence about the grub menu was incomplete. I always set grub up to have a 10-second delay while I choose what to run. (I dual-boot 10.04 and 10.10.)

I wish I had a suggestion other than one which is too late. I have been using Ubuntu for more than three years, and I've never done a version upgrade, only fresh installs. 

I have a separate /home partition, and excellent backup, so I don't lose my data. Reinstalling software takes a little bit of effort, but it's worth it to have a clean system.

---

### Post by fidamehran on 2011-05-26
I have a somewhat different problem.

I am running Natty in an Asus EEE 1001 HA netbook, with 1 GHz processor and 1 GB RAM. The installation went well, and Unity is coming up nice and good. I am running a Wubi installation.

But when I shutdown or restart, the confirmation comes, I click "Shutdown" or "Restart", then only the desktop screen shows. Nothing else.
No further activity whatsoever, even if I wait for minutes or hours.

I browsed certain threads that identified it as some kind of driver problem, and I followed their instruction to blacklist a certain driver and enable certain driver that is supposed to be the correct driver, even then, no solution. Only, after doing it, the screen goes blank and shows some scripts and hangs there.

I also saw some guy posting something about some plymouth conflicts (completely Greek to me) and told to download and run some .sh file. Couldn't understand fully, so didn't take the risk.

In another thread, there was mention of it being some kind of a bug that cannot unmount the WLAN connection, so freezes there. One guy posted a script to add to unmountnfs.sh file in /etc/init.d/ folder ([http://ubuntuforums.org/showthread.php?t=1741668&page=7]("http://ubuntuforums.org/showthread.php?t=1741668&page=7")). The file is locked and I don't know how to edit it. I also don't know whether to add the whole script that the person showed in the box, or a part of it.

Really confused.

---

### Post by gizmobay on 2011-05-26
fiderhman, not sure if this is the same issue you're having

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203)

I looked to my boot.log and it says that the sda didn't unmount cleanly everytime so not sure if that helps.

---

### Post by jcwinnie on 2011-05-31
Hm, I looked at my /var/log/boot.log and it just showed me the current situation and not past issues. Am I looking in the wrong place?

My problem is Natty fails to power off when I shutdown. As someone else mentioned, I can wait for a few minutes or few hours. It does not power down.

A relevant bug report is [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203)

BTW: In the previous thread, someone reported success with adding apm power_off=1 to /etc/modules. That did not help me.

Also in the previous thread, someone else reported resolution of the problem after a Plymouth update. That did not help me. I have a new install with all current updates applied. I also have removed "quiet splash" from grub, not in the way suggested in the previous thread. I sudo gedited /etc/default/grub, removed those parameters, saved then ran 'sudo update-grub'

What does work is what I have done to previous Ubuntu versions. Added acpi=force. Doing this to the current installation in the same way that I removed "quite splash" resulted in the PC powering off at shutdown.

Doing this seems to foreshorten the shutdown process on Natty, so I hope that there will be a developer solution and not have to rely on a user hack.

---

### Post by gizmobay on 2011-11-07
Whatever was changed in 11.10 resolved this problem.

---

