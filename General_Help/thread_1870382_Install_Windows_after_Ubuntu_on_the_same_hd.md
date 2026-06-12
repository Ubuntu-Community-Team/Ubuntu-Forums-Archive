---
title: "Install Windows after Ubuntu on the same hd"
date: 2011-10-27
forum: General Help
---

### Post by Lucas Malor on 2011-10-27
I tried to install Windows XP Pro on an hard disk with Ubuntu already installed. I created with the LiveCD a partition for it, but the Windows installation alerts me it can't use that partition.
For now I have Windows on another hd, but it's an old slower one and I want to use it as backup hd.
Is this a problem concerning an old Windows install CD or did I do some error creating the partition?

---

### Post by vicshrike on 2011-10-27
In my experience it is always easier to install windows first, and then let the Ubuntu installer partition the hd for me.

---

### Post by satanselbow on 2011-10-27
Did you create your windows partition at the start of the disk or somewhere in the middle as XP has major problems with partitions placed further up the disk :(

What is the exact error?

vicshrike is correct that it is simpler to installer xp first but doing it 2nd is do-able ;)

Get familiar with the procedure required to reinstate grub to mbr BEFORE YOU START - unless you are planning on using easybcd?

---

### Post by linuxwin2 on 2011-10-27
You must install windows on first partition of your disk.
Else you can't.
After you must install grub.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Cpierce on 2011-10-27
You can install windows after and it doesn't have to be the first partition.  Read my comments here:
[http://ubuntuforums.org/showthread.php?t=1838771](http://ubuntuforums.org/showthread.php?t=1838771)

---

### Post by Mark Phelps on 2011-10-27
How did you format that partition? Later versions of XP work fine with NTFS, but I believe the initial version might want FAT32.  Been so long, don't recall.

---

### Post by Lucas Malor on 2011-10-27
Ok, I think the problem is the partition wasn't the first one.

I do **not **want it on the first partition. I use Windows only to play games sometimes and I don't want to slow down Ubuntu for this. Yes I know Wine, but often it doesn't work...

Is there no way to install Windows XP on a partition that it's not the first one?

@Cpierce: you installed Windows 7.

---

### Post by varunendra on 2011-10-27
> **Lucas Malor said:**
> Ok, I think the problem is the partition wasn't the first one.
Is there no way to install Windows XP on a partition that it's not the first one?
I have installed winXP on extended partitions in the past. But in those cases, the first one was FAT32 with DOS or Win98. So I can confirm that winXP itself does not need to be in the first partition. However, there is a catch-

AFAIK, it is important (for windows boot-loader) that two of three boot files of xp (boot.ini and ntdetect.com, if I remember correctly) need to be in the initial primary partition(s) which are located within a particular cylinder boundary. Else, it won't be bootable. So, although I didn't notice it when I had that kind of setup, these two files were always located in the FAT32 partition which was in the beginning.

I also believe you don't need those two files nor a first partition dedicated to boot xp if you are going to boot it through grub. But, you do need one (even if a small one, maybe of the least possible size) FAT32 or ntfs partition in the beginning, at least temporarily, to satisfy XP installer. Once you got it installed in a later partition, you can safely remove the partition in the beginning and update grub if required. You will need only ntldr in the partition where XP is loaded, so copy it before deleting the boot partition (the temporary one). Of course you will have to reinstall and update grub afterwards since XP MBR will have overwritten it while installation process.

Please be aware that I am suggesting this only from a faded memory and some guesses. So it has no guarantee of success. May be it will be a lot easier to advise you if we can have a look at the screenshot of gparted.

For now, I think this 'should' work:-

[LIST]
[*]Using gparted, create a 200MB fat32 partition in the beginning (gparted won't let you exceed the number of primary partitions beyond 4)
[/LIST]

[LIST]
[*]Install XP in your desired partition (it shouldn't complain this time)
[/LIST]

[LIST]
[*]Copy ntldr file from the fat32 partition to the XP installation partition
[/LIST]

[LIST]
[*]Delete the fat32 partition (if you feel necessary, else, leaving it won't hurt)
[/LIST]

[LIST]
[*]Reinstall grub using Live CD (refer to [this guide]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2"))
[/LIST]

[LIST]
[*]Boot into Ubuntu, and update grub ```
sudo update-grub
```
[/LIST]
Now you 'should' have Ubuntu and XP both, the way you desire.

---

### Post by oldfred on 2011-10-27
varunendra's info is correct, but I think you also need a boot flag.

Windows only knows which partition to boot (or repair) as the partition with a boot flag (active partition in Windows). Grub does not use boot flag. Windows boot loader checks that partition is primary, so it only boots from a primary partition. But lilo boots the same way and does not check, so one advanced user here does have instructions on booting XP in a logical partition.

Many have been able to just use a NTFS formated primary (sda1 thru sda4) partition with the boot flag. A few have had issues and it may be if the primary partition is after the extended & logicals, not sure why otherwise. Also BIOS settings can interfere as my XP does not now boot as I turned on ACHI for my new SSD.

---

### Post by varunendra on 2011-10-27
> **oldfred said:**
> ....my XP does not now boot as I turned on ACHI for my new SSD.
Interesting! I very recently experienced otherwise. While experimenting with one of the HP dx2480 desktops in our office, I turned off AHCI in the BIOS. Later when I tried to boot it into installed XP (SP3), it began to restart on every boot attempt. Fortunately, the AHCI change immediately flashed in my mind and I changed it back to 'On'. It booted fine again.

So I think it is just XP's lack of flexibility regarding some drivers and core configuration. If so, yours should also be able to boot with AHCI on if reinstalled fresh.

---

### Post by oldfred on 2011-10-27
I did find a site on how to install the drivers, actually best to install them as part of a new install of XP. But I use XP so little I do not really care. I may just to try it install the new drivers just to see if I can get XP to boot, but it just may force me to finally give up on XP as I promised several years ago.:)

---

### Post by Lucas Malor on 2011-10-30
> **varunendra said:**
> [...] you do need one (even if a small one, maybe of the least possible size) FAT32 or ntfs partition in the beginning, at least temporarily, to satisfy XP installer.  ... damn it. 
  Well, I'll write you if I messed up my PC or not :)

---

### Post by Lucas Malor on 2012-03-25
Ok, I don't do it on my pc since I have no time, but I had to reinstall ubuntu + winxp on a pc of a friend of mine, so I tried this "trick" and it doesn't work.

There were two hd, an **old 10 GB ide** and a 1 TB sata2. Ubuntu install recognized **the first one as sda**, so it installed grub on it, and the second one as sdb. On sdb I created a temporary fat32 **primary** partition **with** boot flag of 200 MB, one ext4 primary partition without boot flag, one swap partition and another fat32 **primary** partition **with** boot flag.
I installed ubuntu and I started winxp install. I selected the second fat32 partition and I reformatted it as **ntfs**. After the winxp copied the install files and restarted the pc, the install doesn't go further. So I started ubuntu and after an update-grub I tried to resume the windows install selecting it with grub, but nothing...

Now I installed winxp as first partition. Maybe ntldr had to be copied to the second partition immediately?

---

### Post by oldfred on 2012-03-25
Windows only recognizes a boot flag on a primary partition. And you cannot have two boot flags on one drive.

If an older system, it may have a BIOS that only lets you boot from the first 137GB either Windows or Ubuntu. Data partition can be later on the drive but the system partitions have to be fully inside the 137GB limit.

XP normally installs to one active (boot) flag partition. Windows 7 normally creates a 100MB hidden boot partition and the main install partiiton. If you want a separate Windows boot partition you will have to copy or move the boot files to the boot partition.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

