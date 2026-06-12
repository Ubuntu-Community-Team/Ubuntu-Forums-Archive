---
title: "Dual booting Vista and Ubuntu 10.04"
date: 2010-05-12
forum: General Help
---

### Post by frogbrains on 2010-05-12
I know, I know, I'm really sorry.

Anyway, originally my laptop came with Vista preinstalled.  Immediately installed Ubuntu, but left Vista on there as a dual boot for games and video editing and such.  In 9.10, I could boot Vista fine.  Now, grub does not let me boot Vista.  A "windows recovery" thing or something like that is an option in grub, but going on that just brings up a black screen with an underscore in the top left hand corner blinking at me forever.  Have to force reboot.  10.04 works beautifully, lovely and fast, sound works properly (unlike 9.10 before updates) but I really, really need to boot Windows right now.  I can still access my Windows partition from Ubuntu, so it's not that it's been deleted.  I have tried running update-grub, but that did not help at all.

Please, tell me how to fix this!
Thanks
Adam

---

### Post by lmarmisa on 2010-05-12
Open a terminal and type this command:

> 
sudo update-grub2


Reboot the system and check if you have both boots.

Best regards,

Luis

---

### Post by frogbrains on 2010-05-12
Thanks, I'll try that.

---

### Post by frogbrains on 2010-05-12
> **lmarmisa said:**
> Open a terminal and type this command:



Reboot the system and check if you have both boots.

Best regards,

Luis

No, sorry, that worked no better than sudo update-grub.

Does anyone else have any ideas?

Just in case it's important, here's the output from sudo update-grub.  (It is exactly the same in sudo update-grub2.)
```
adam@adam-laptop:~$ sudo update-grub
[sudo] password for adam: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda2
Found Ubuntu 10.04 LTS (10.04) on /dev/sda5
done

```

---

### Post by lmarmisa on 2010-05-12
The update-grub command is not able to found the Vista partition but you can mount it and see its contents.

Could you copy the output of this command?

> 
sudo fdisk -l
You can read here some interesting information about Windows Dual Boot, but I am not sure if it will be useful for solving your problem:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

My dual boot system is XP + Ubuntu. In this case, it is very easy to restore the XP loader program in the MBR. But the case of Vista and Windows 7 is different.

---

### Post by frogbrains on 2010-05-12
> **lmarmisa said:**
> The update-grub command is not able to found the Vista partition but you can mount it and see its contents.

Could you copy the output of this command?

You can read here some interesting information about Windows Dual Boot, but I am not sure if it will be useful for solving your problem:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

My dual boot system is XP + Ubuntu. In this case, it is very easy to restore the MBR of the XP loader in the program. But the case of Vista and Windows 7 is different.

Yes, here is the output:
```
adam@adam-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ab852fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           26140       30401    34226881+   5  Extended
/dev/sda2   *         263       26140   207859229    7  HPFS/NTFS
/dev/sda3               1         262     2104483+  82  Linux swap / Solaris
/dev/sda5           27035       30401    27045396   83  Linux
/dev/sda6           26140       26989     6819840   83  Linux
/dev/sda7           26990       27034      360448   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06a71716

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2    31008256   976760032+   7  HPFS/NTFS

```

Edit: The 1000GB drive is my USB external, you can ignore that.

---

### Post by frogbrains on 2010-05-12
> **lmarmisa said:**
> The update-grub command is not able to found the Vista partition but you can mount it and see its contents.

Could you copy the output of this command?

You can read here some interesting information about Windows Dual Boot, but I am not sure if it will be useful for solving your problem:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

My dual boot system is XP + Ubuntu. In this case, it is very easy to restore the XP loader program in the MBR. But the case of Vista and Windows 7 is different.

Also, when I boot my computer, an option with the word "Windows" in it is available, but when I select it it takes me to a black screen with a flashing "_" in the top left corner.

---

### Post by oldfred on 2010-05-12
When you upgraded did you not just check drives but also check all the partitions? if so:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by lmarmisa on 2010-05-12
I have made some tests using my wife's laptop computer. This computer has installed Vista Home Premium and I have plugged an external USB HDD with Ubuntu 10.04. The BIOS is programmed to boot from the USB devices as first priority.
 
I typed the command update-grub2 and two Vista partitions were detected:

[LIST=1]
[*]A loader(?) partition on /dev/sda1 labeled PQSERVICE of 10 Gbytes where grub2 says "Windows Vista (loader)"
[*]A big partition on /dev/sda2 where grub2 says "Windows Recovery Environment (loader)"
[/LIST]
If I try to boot from /dev/sda2 the system reboot again.

If I try to boot from /dev/sda1 the result  is a bit better, but not perfect, because a recovery procedure is started after 15 seconds or so. Maybe this is due to the BIOS mapping of the HDDs detected and it would work well if Ubuntu were installed in the /dev/sda hard drive. 

You have only one partition for Vista and it is not detected by grub as "Windows Vista (loader)". Something looks wrong there. Or the Vista loader partition is deleted or the loader of the ntfs Vista partition is damaged.

I have found this page that can help you:

[http://windowsteamblog.com/Windows/archive/b/windowsvista/archive/2006/12/05/windows-recovery-environment.aspx](http://windowsteamblog.com/Windows/archive/b/windowsvista/archive/2006/12/05/windows-recovery-environment.aspx)

---

### Post by frogbrains on 2010-05-12
Thank you both for your responses, but for now I'm just going to say "**** Windows."  Ubuntu still works perfectly, that is all I need.

I will be getting a new and awesome computer in the next few months, so everything will be fresh and lovely again.

---

### Post by obaid on 2010-05-12
according to your fdisk -l output, you have got 1 ntfs partition and that is the recovery partition on /dev/sda. you dont have a partition with windows vista OS.

Edit: but your external drive /dev/sdc have also got a boot flag, is there OS installed on external drive ?

---

### Post by lukeylad118 on 2010-05-17
I just fixed my friends laptop with the same problem and I really couldn't believe how easy it is to fix. All you do is: 
boot up windows 
after the boot screen has finished wait 2-3 seconds 
then press Y and hit enter. 
Vista will then proceed to boot to the logon. I am 100% not lying I have just done it now and in a couple of days me and my friend are to upload a video of us doing so to youtube.

I was in hysterics when I did it, anyway try it and tell me how it goes, should work though done it about 10 times with my friends laptop just to make sure it wasn't a fluke. But I can confirm this is 100% genuine fix for your problem.

Hope it helps,
Lukeylad118

> **frogbrains said:**
> I know, I know, I'm really sorry.

Anyway, originally my laptop came with Vista preinstalled.  Immediately installed Ubuntu, but left Vista on there as a dual boot for games and video editing and such.  In 9.10, I could boot Vista fine.  Now, grub does not let me boot Vista.  A "windows recovery" thing or something like that is an option in grub, but going on that just brings up a black screen with an underscore in the top left hand corner blinking at me forever.  Have to force reboot.  10.04 works beautifully, lovely and fast, sound works properly (unlike 9.10 before updates) but I really, really need to boot Windows right now.  I can still access my Windows partition from Ubuntu, so it's not that it's been deleted.  I have tried running update-grub, but that did not help at all.

Please, tell me how to fix this!
Thanks
Adam

---

