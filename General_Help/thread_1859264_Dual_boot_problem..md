---
title: "Dual boot problem."
date: 2011-10-13
forum: General Help
---

### Post by gavdari on 2011-10-13
I have installed ubuntu 11.10 alongside with Windows 7 on my new machine. Grub is working fine, but I need to return back to only windows 7 for now (because of many issues in 11.10, like graphic card not supported yet, strange bugs with kernel, etc.), with all the exams and everything I can't have both on my system. Is there any way to format the ext partitions and merge them again with the windows partition? My guess is if I just format linux partitions from the windows it will mess up the MBR and maybe I'll lose my windows too. any suggestion?

---

### Post by Musmanno on 2011-10-13
In Windows 7 click on the Start menu, then right-click on Computer and select "manage." You should be able to manage the hard disk partitions directly from Win 7 by doing that, and you can eliminate the Linux partitions and change sizes of Windows partitions without messing up the installation.

---

### Post by zhogan85 on 2011-10-13
I know how to do this with linux systems, but I think its a little trickier with Windows.

This thread on another forum seems like it might be helpful. 

[http://social.technet.microsoft.com/Forums/en-US/w7itproperf/thread/19b60bc3-86a2-45d1-b2b5-16f9f3671a2b/](http://social.technet.microsoft.com/Forums/en-US/w7itproperf/thread/19b60bc3-86a2-45d1-b2b5-16f9f3671a2b/)

To do what they are suggesting, you would probably have to delete Ubuntu and reformat the partition it was on with Gparted to be NFTS (using a livecd).

Then from there, you could merge the two partitions, or since windows can read NFTS, the safer option would be to use the new partition as a data partition in windows.

---

### Post by gavdari on 2011-10-13
Are you sure that this won't mess up the master boot record on the hard drive? right now it is set to boot using grub, so if I format the whole linux partitions in windows then there will be no grub. I guess there should be some way to restore the MBR before formatting the ext4 partitions.

---

### Post by Musmanno on 2011-10-13
You don't have to go to that amount of trouble. You can remove the Linux partitions from within Windows, then create a new partition and format it NTFS without harming the Windows installation. The only thing you can't do is merge the partitions, but if you completely remove the Linux partitions you can try to increase the size of the Windows partition to take up some of the free space.

In any event, there is no need for gparted or any third party tool to get rid of the linux installation and just have a new NTFS partition in Windows.

EDIT: If you have your Win 7 discs you can fix the MBR and get rid of GRUB.

---

### Post by gavdari on 2011-10-13
Thank you for the answers. I'll try these.
11.10 is running perfectly fine on my other laptop, but on the new one I had so much problems that I decided to give it some time. 
unfortunately, since windows was shipped with this laptop, there is no installation dvd for it, but I'll try with another dvd, maybe I'll be able to fix MRB afterwards.
thank you.

---

### Post by Musmanno on 2011-10-13
No problem gavdari. With the other DVD you can probably just chose to repair the installation and then go to the command prompt from there. If you search Google you'll see instructions on how to restore the MBR from the command prompt. I think you can also let the DVD attempt to fix the installation automatically, but if the DVD isn't the same product code of the installation on the computer, I don't know what the effect will be. It may work or it make recognize that the codes don't match.

---

### Post by oldfred on 2011-10-13
You really want to fix MBR first. You can do it from the Windows repair console f8 as you boot. Or you can install lilo which  works just like Windows boot loader in chaining to the PBR to continue to boot.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

Always have a repairCD or USB for every system you have installed and possibly a few others.
Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by gavdari on 2011-10-13
Thank you oldfred. For future reference, this is what happened:
After formatting the ext4 drive using NTFS file system and rebooting, the system went into grub rescue terminal mode. I restarted the system and boot into ubuntu using a live usb. the first thing I tried was lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
which worked perfectly fine. MBR was updated and everything seems to be ok.
there is only one problem though, I have 2 partitions on my hard disk now, which for now I have not been able to merge them. but I can live with that. ;)
Thank you all for answering. I'll mark this Solved.

---

### Post by oldfred on 2011-10-13
Glad that worked.

Many Windows users like a separate data partition. It helps separate system from data. But you need to remember to run chkdsk on it occasionally.

---

