---
title: "Replacing WinXP partition"
date: 2012-04-28
forum: General Help
---

### Post by Tombgeek on 2012-04-28
Hi there

This is probably a stupid question, so please forgive me. Anyway, I used to use Ubuntu for a while but then moved to Windows 7. Over the past two years I've basically messed up my partitions a bit. You can see my partitions in the attachment. Anyway, I'm currently running Windows 7 as my primary OS. However, Windows XP is on the supposed D: drive (though I think it's actually labeled C: when you look on GParted). Windows 7 is on the other and the partitions in the green box was my previous Ubuntu partition (now I'm just using it for storage). 

Anyway, I want to get rid of Windows XP and install Ubuntu on the 65GB partition. If I just install Ubuntu 12.04 over it, will Windows 7 still boot?

---

### Post by xyzzyman on 2012-04-28
Do you already have 12.04 downloaded and burned or on a USB drive? A screenshot of the drive in gparted off your livecd would allow us to better help you. Definitely have a current data backup just in case, but this should be very straight forward to clean up your partitions and dual-boot. Just that gparted will allow us to see the real structure a bit better.

And it's not a stupid question. You recognized that the image of your layout provided by disk management in Windows was a little too simplified, and better to be safe than sorry until you get a good idea of partition layouts for dual-boots. Some people will only dual-boot with multiple hard drives, but a lot of us know that's not feasible for everyone and do it ourselves especially in notebook computers.

---

### Post by Tombgeek on 2012-04-28
Hi, thanks for replying.

Here's a screenshot from GParted.

I've got all my important files backed up and I still have the Windows 7 disc, so I can do a startup repair if something goes wrong. I really just wanted to know if there was a way I can avoid that (and there was one case with XP where the repair didn't want to work, so I had to reinstall anyway).

---

### Post by xyzzyman on 2012-04-28
So verify we're on the same page:

SDA1 is your Windows 7 partition (Keep)
SDA2 is Windows XP (Delete)

What is SDA5, a shared NTFS partition for data between Windows/Linux?

If so, seeing as you have your data already backed up anyways, what I personally would do is:

1. Format sda2 as ext4, and resize it down. I give 12GB's to my / directories but unless you really know give it 20-30GB's. Apply.
2. Resize the extended partition to fill up the unused space at the front and back of it. Apply.
3. Create an sda4 at whatever size you like to use a /home directory. Apply.
4. Decide if you want to resize SDA5 to fill up the space, or create other ntfs partitions. I do 3 different NTFS partitions myself now. One for downloading torrents and other files that will probably get deleted, one for more permanent storage, and another that I save my virtual machines on. It might not even hurt to make some ~15GB partitions in that space just so you have spots open in the future to install other distro's, try an ubuntu beta, etc... Just don't use a seperate home partition when you do that.

Then go ahead and install Ubuntu 12.04, remembering to use sda2 as /, sda4 as /home, and install GRUB to /sda. It should make a Windows 7 entry no problem. If not, come back here for help setting up grub without restoring to just putting the Win7 bootloader back on.

---

### Post by Tombgeek on 2012-04-28
> **xyzzyman said:**
> So verify we're on the same page:

SDA1 is your Windows 7 partition (Keep)
SDA2 is Windows XP (Delete)

Actually, it's the other away around, but it doesn't really matter.

> **xyzzyman said:**
> What is SDA5, a shared NTFS partition for data between Windows/Linux?

It's just an old partition I have lying around (mostly because I didn't know what I was doing). I'm just keeping my brother-in-law's music in there because he his collection is disorganized and he wants me to sort it for him (but high school has been keeping me too busy lol). But I guess it would be useful as a file cross-over partition for Win/Linux.

> **xyzzyman said:**
> 

1. Format sda2 as ext4, and resize it down. I give 12GB's to my /  directories but unless you really know give it 20-30GB's. Apply.
2. Resize the extended partition to fill up the unused space at the front and back of it. Apply.
3. Create an sda4 at whatever size you like to use a /home directory. Apply.
4. Decide if you want to resize SDA5 to fill up the space, or create  other ntfs partitions. I do 3 different NTFS partitions myself now. One  for downloading torrents and other files that will probably get deleted,  one for more permanent storage, and another that I save my virtual  machines on. It might not even hurt to make some ~15GB partitions in  that space just so you have spots open in the future to install other  distro's, try an ubuntu beta, etc... Just don't use a seperate home  partition when you do that.

Then go ahead and install Ubuntu 12.04, remembering to use sda2 as /,  sda4 as /home, and install GRUB to /sda. It should make a Windows 7  entry no problem. If not, come back here for help setting up grub  without restoring to just putting the Win7 bootloader back on.

Thanks. :) Okay, so are you sure that if I install Ubuntu onto SDA1 that Windows's boot procedure won't corrupt because it's expecting Windows XP to be there?

---

### Post by xyzzyman on 2012-04-28
> **Tombgeek said:**
> Actually, it's the other away around, but it doesn't really matter.



It's just an old partition I have lying around (mostly because I didn't know what I was doing). I'm just keeping my brother-in-law's music in there because he his collection is disorganized and he wants me to sort it for him (but high school has been keeping me too busy lol). But I guess it would be useful as a file cross-over partition for Win/Linux.


Thanks. :) Okay, so are you sure that if I install Ubuntu onto SDA1 that Windows's boot procedure won't corrupt because it's expecting Windows XP to be there?

No, install it to SDA. It'll be an option to not do a partition # and will default most likely anyways. 

What is your current bootloader? Windows 7's on sda1, or a grub?

---

### Post by jerome1232 on 2012-04-28
Do you have a Windows recovery cd? I understand you can create a system recovery disc (which can restore the mbr in case it gets messed up) in the backup and maintance wizard 
Source: [http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc)


After you create that, also have an Ubuntu live cd handy. Then if you do manage to destroy your boot loaders, you have all the tools required to fix it all.

---

### Post by xyzzyman on 2012-04-28
> **jerome1232 said:**
> Do you have a Windows recovery cd? I understand you can create a system recovery disc (which can restore the mbr in case it gets messed up) in the backup and maintance wizard 
Source: [http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc)


After you create that, also have an Ubuntu live cd handy. Then if you do manage to destroy your boot loaders, you have all the tools required to fix it all.

He already stated that he has his Windows 7 disk for restoring the boot loader if necessary. He's just learning how to try to avoid that which is a good exercise because you get a good feel for how grub2 works in a multiboot environment.

---

### Post by jerome1232 on 2012-04-28
Thanks for catching my oversight, Didn't see that in the OP. I thought you guys were attempting this without a "if it fails" plan and was trying to edge a little caution in.

---

### Post by Tombgeek on 2012-04-28
> **xyzzyman said:**
> What is your current bootloader? Windows 7's on sda1, or a grub?

Windows 7's. I haven't had Ubuntu or any Linux distro installed on my PC for the last year or so. Exclusively Windows. This is me going back to Linux for university next year (studying Computer Science).

> **jerome1232 said:**
> Do you have a Windows recovery cd? I understand you can create a system recovery disc (which can restore the mbr in case it gets messed up) in the backup and maintance wizard 
Source: [http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc)


After you create that, also have an Ubuntu live cd handy. Then if you do manage to destroy your boot loaders, you have all the tools required to fix it all.

Thanks. I do still have the original install disc. I might also create a repair disc. I'm paranoid lol.

---

### Post by oldfred on 2012-04-28
If XP was your first Windows in sda1 and it has boot flag, then all the Windows 7 boot files are in sda1 with XP. Windows only boots from the active partition (boot flag) and Windows 7 takes over booting from the active partition.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

I would copy bootmgr & /Boot/BCD to sda2 and move boot flag to sda2. See if 7 still boots or it may need repairs to boot before deleting sda1.

---

### Post by Tombgeek on 2012-04-29
> **oldfred said:**
> If XP was your first Windows in sda1 and it has boot flag, then all the Windows 7 boot files are in sda1 with XP. Windows only boots from the active partition (boot flag) and Windows 7 takes over booting from the active partition.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

I would copy bootmgr & /Boot/BCD to sda2 and move boot flag to sda2. See if 7 still boots or it may need repairs to boot before deleting sda1.
 
I'm not sure if that'll work. As far as I know, XP and 7 have different booting methods. Because I installed XP first, 7 recognized that I have an older version, thus I'm able to boot into both. If it was in reverse, it apparently wouldn't work. 

So it looks like I might have to repair after all. Oh well. Thanks for your help guys. :)

---

### Post by oldfred on 2012-04-29
One user who deleted first, said he just copied his bootmgr and BCD from his repairCD. Of course he had to edit the BCD as it was only for the repair and not his install.

Sometimes fixBoot and/or chkdsk is also required to make sure the Windows 7 partition boot sector is correct.

I ran chkdsk on my XP install from a Windows 7 repair USB and it put a Windows 7 partition boot sector into my XP. Go figure.

---

### Post by Tombgeek on 2012-05-04
Hi

Sorry to bump this thread, but I really just want to be sure.
A friend at school told me that I won't have any problems because grub will apparently automatically see that Windows 7 is installed and both OSs (Ubuntu and Windows) will boot fine. Is this true?

---

### Post by oldfred on 2012-05-04
Once 7 is fixed to boot correctly without the XP partition, yes grub2's os-prober will find the Windows 7 install and add it to your menu.

Run this:
sudo update-grub

If you want more info on how XP and Vista or 7 work in dual booting, lots of detail, but pictures are a good start:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Tombgeek on 2012-05-04
> **oldfred said:**
> Once 7 is fixed to boot correctly without the XP partition, yes grub2's os-prober will find the Windows 7 install and add it to your menu.

Run this:
sudo update-grub

If you want more info on how XP and Vista or 7 work in dual booting, lots of detail, but pictures are a good start:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)


OK, thanks :)

Sorry I'm so bothersome. I'm just being cautious.

---

### Post by oldfred on 2012-05-04
Did you copy these from your XP partition to your 7 partition?
/bootmgr /Boot/BCD

Did you make your own Windows 7 repairCD or USB?

---

### Post by Tombgeek on 2012-05-05
> **oldfred said:**
> Did you copy these from your XP partition to your 7 partition?
/bootmgr /Boot/BCD

Did you make your own Windows 7 repairCD or USB?

I did create a repair CD and I didn't copy BSD to 7, mostly because I couldn't find any other discussion on this using this method. So I'm a bit scared to try it. I think I'll just use the repair CD

Thanks for the help guys. :)

---

### Post by oldfred on 2012-05-05
Move boot flag to Windows 7  and do repair first before deleting XP, to be sure it works first.

We have many posts here where they damage the boot of 7 by deleting another Windows install.

---

