---
title: "Problems of ubuntu 11.10"
date: 2012-02-09
forum: General Help
---

### Post by jairoh_ on 2012-02-09
Hi I'm dual booting in windows and ubuntu 11.10 but why can't i shrink the volume of the partition in ubuntu?

And I can't connect to internet in ubuntu. I'm using sun broadband wireless. And everytime I try to change the internet settings in ubuntu, and then I'll go back in booting in windows I can't boot windows, Blue screen(w/ error i don't know specifically)would appear after the windows loading, and then it reboots again after the blue screen happened and again it reboot after the windows loading. So my solution is, I'll turn off my pc using ubuntu since i cannot boot to windows after changing some internet settings in ubuntu like apn and etc. and after 5 minutes i can boot again to windows. why is that happening? 

And I can't install programs and drivers in ubuntu, it would only appear "More Information" w/o "Add Program", but i can remove the existing programs w/c has "Remove Program". 

Anyone can help? is this one of the compatibility problems of ubuntu 11.10? PLS HELP!

---

### Post by sunewbie on 2012-02-09
Rebooting problem is not because of Ubuntu malfunction.

Ubuntu uses GRUB bootloader and and only reason you cannot boot into windows is if GRUB gets corrupted.

Recently, there is a big virus problem which jams network LAN and Internet and also WLAN (wireless LAN). Anybody using net protector anti virus was attacked. Karpersky internet security 2012 users need not format PC. Update AV and then run full scan removing all LAN cable. 

If you are using net protector, restore your PC for any restore point before 23rd JAN 2012. Update it and run full scan. If you do not face problems then virus is cleaned. Else format it.

Virus does not influence Linux, so it is a driver compatibility issue.

You can try to download ndiswrapper

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

[http://askubuntu.com/questions/76313/how-to-keep-ndiswrapper-configuration-after-reboot](http://askubuntu.com/questions/76313/how-to-keep-ndiswrapper-configuration-after-reboot)

[http://www.ubuntuupdates.org/package/core/oneiric/main/base/ndiswrapper](http://www.ubuntuupdates.org/package/core/oneiric/main/base/ndiswrapper)

download and install it. Reboot and try to connect to net.

After connecting, run update manager and things should be fine.

Installation of any app needs internet connection. So after you manage to connect to internet, you can install / add apps from Ubuntu Software Center.

Second note about blue screen of death
This might be hardware failure. e.g. if RAM is corrupted (mostly if you have 2 RAMs). In this case you cannot even try LIVE Cd, as it requires RAM to work.

There may be problem with HDD or any wired connection.
As explained earlier, windows crashed due to instability mostly due to virus attack, like kernel panic (blue screen of death).

In this case, full format that drive and reinstall windows. After re installation, Boot loader GRUB will be overwritten by windows loot loader and so you will not be able to boot into Ubuntu. So Boot through LIVE CD and then reinstall GRUB. 

Search for 'Reinstall GRUB2 after installing windows' or 'reinstall GRUB from LIVE Cd' or 'reinstall GRUB after windows'

Hope this helps.

---

### Post by Mark Phelps on 2012-02-09
You're already receiving some really good help ... so I'll just offer a few comments ...

In terms of shrinking a volume -- which volume?  If it's an Ubuntu volume, you can't do that while running Ubuntu because the volume is in use.  You will have to boot from CD to make such changes.

If it's a Windows volume, and that is Win7, then do NOT attempt to shrink it from inside Ubuntu.  That risks file damage and, if done, may render Win7 unbootable.  For Win7, use only its Disk Management utility to shrink its volumes.

If you've been getting the bluescreens in Windows ONLY since you installed Ubuntu, and it is Win7, then you likely corrupted the filesystem in the process.  You can try using Boot-Repair to see if that can fix it: 

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

But ... if that does restore Windows booting, you will have to reinstall GRUB from a CD to get Ubuntu booting again.

As to Sun broadband wireless, on my PC, I use Verizon broadband wireless -- and it ONLY works with Windows.  The wireless modem requires both special drivers and software -- both of which only work in Windows.  If your modem has similar limitations, there will be nothing you can do to get it working in Linux.

---

### Post by sunewbie on 2012-02-09
Helping others does help me a lot. I learn a lot, like I did in this thread.

Just to add another cent.

If GRUB is corrupted or if windows bootloader is corrupted, then even reinstalling GRUB sometimes does not solve problem.

In this case, you need to repair windows boot loader. You can do it by going for 'repair windows' option.

After restoring Boot loader, then boot using LIVE CD and then reinstall grub.

Alternatively, some people use EasyBCD, free boot loader for windows 7 (and vista). It recognises Linux. If something happens to Linux or you uninstall it for some reason, you can still boot in to win 7.

I had read a n article. If I get the link I will post it.

---

### Post by jairoh_ on 2012-02-09
i think my os is fake. i'm not advertising piracy here. but is there a way to repair this if my os is not genuine? 

and i now knew that everytime i boot into unbuntu(not even changing settings in it), i cannot boot into windows blue screen appears unless i'll shutdown it for 5 mins.

---

### Post by grahammechanical on 2012-02-09
> And I can't install programs and drivers in ubuntu, it would only appear "More Information" w/o "Add Program", but i can remove the existing programs w/c has "Remove Program". 

You need to be connected to the internet to install/add a program as the program is first downloaded and then installed.

We do not need to be connected to the internet to remove programs because the removal process deletes files.

If you are talking about repairing the Windows OS, then you must use the Windows tools for that.

Boot into windows. Use it for some time and then shut down and reboot. Do you then get the blue screen?

Regards.

---

### Post by sunewbie on 2012-02-10
> **jairoh_ said:**
> i think my os is fake. i'm not advertising piracy here. but is there a way to repair this if my os is not genuine? 

and i now knew that everytime i boot into unbuntu(not even changing settings in it), i cannot boot into windows blue screen appears unless i'll shutdown it for 5 mins.

If you insert XP / Win 7 and if Win XP / 7 is preinstalled, then the CD will show you repair option.

else you can create rescue disk / recovery disk and driver backup disk (all in Win 7) in win 7 and use it to reinstall OS. There is also an option of one touch restore. This is the reason why there is a restore partition.

Alternatively, you can try to restore to an earlier date, may be a month earlier. type msconfig in run box (start --> run) and then check for system restore. you can also search for system resotre and XP / 7 saves restore points automatically (which can save it manually to and name it)

this should work with fake DVDs too. It's a common procedure.

---

