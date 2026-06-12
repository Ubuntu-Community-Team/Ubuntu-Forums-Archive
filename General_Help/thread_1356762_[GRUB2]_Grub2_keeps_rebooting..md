---
title: "[GRUB2] Grub2 keeps rebooting."
date: 2009-12-16
forum: General Help
---

### Post by stefano.gam on 2009-12-16
Hi all.

I am experiencing this problem: GRUB2 keeps rebooting my machine every time it loads.
It happens right after the "GRUB Loading Please Wait" "screen", and right before the OS List.

I tried to reinstall GRUB2 using a livecd, and it works fine up to when I reboot again.
Reinstalling GRUB2 again and again is pointless, since it doesn't solve my issue.
Any ideas? Maybe installing GRUB Legacy over GRUB2?

TYIA.

---

### Post by Chesamo on 2009-12-16
From the LiveCD, try checking your GRUB configuration files and running sudo update-grub.

---

### Post by stefano.gam on 2009-12-16
> **Chesamo said:**
> From the LiveCD, try checking your GRUB configuration files and running sudo update-grub.

Tried, every time.

---

### Post by joes7 on 2009-12-16
```

Applications->Add/Remove Applications-> search for "starup manager"

```
Change GRUB timeout to 0. 

Voila.

---

### Post by joes7 on 2009-12-16
Re-install from the LiveCD

---

### Post by ean5533 on 2009-12-16
> **joes7 said:**
> Re-install from the LiveCD
Did you even read his whole post? He already said that he's re-installed GRUB from the LiveCD multiple times and it only works the first time he reboots after the install. 

And unless I'm missing something obvious, how would changing the GRUB timeout to 0 solve his problem of the computer restarting?

---

### Post by john newbuntu on 2009-12-17
Please confirm that you are able to boot in at least once successfully (without liveCD) before it stops working. Also, make sure that you did execute the "sudo grub-install --root-directory=/mnt /dev/sda --recheck" command from your liveCD to add grub2 to the MBR. If both of these are true, it appears as if some program is overwriting the mbr between your two boots or your grub.cfg is getting corrupted/modified.
Presuming you have enough timeout in the grub config and that it does not even get to the OS menu screen, I don't think runlevel comes into the picture here.

---

### Post by Leppie on 2009-12-17
are you only using ubuntu, or dual booting with other systems as well?

---

### Post by mikitz on 2009-12-17
Same problem here with Win7/Karmic dual boot. I can boot into Karmic as many times as I want with no problems but as soon as I boot into Win7, it seems to corrupt grub2. The next boot just keeps restarting as soon as grub begins loading. I can reinstall grub with a liveCD but the problem repeats every time I boot into Win7. Any ideas?

---

### Post by Leppie on 2009-12-17
> **mikitz said:**
> Same problem here with Win7/Karmic dual boot. I can boot into Karmic as many times as I want with no problems but as soon as I boot into Win7, it seems to corrupt grub2. The next boot just keeps restarting as soon as grub begins loading. Any ideas?

what hardware are you using?

---

### Post by proxess on 2009-12-17
Reinstall it then update-grub2

---

### Post by mikitz on 2009-12-17
> **Leppie said:**
> what hardware are you using?

Dell Optiplex 755..

---

### Post by mikitz on 2009-12-17
fdisk -l tells me the lab techs here installed Win7 using HPFS/NTFS filesystem. I then installed Karmic using ext3. I couldn't use ext4 b/c they have to use Norton Ghost later to clone all other machines and it doesn't understand ext4 apparently.

EDIT: hmmm I don't know if any of this is related, but it looks suspicious... fdisk -l tells me the Win7 partition (Partition 1 and 2) do not end on cylinder boundary. Also when trying to run dumpe2fs on either win7 partition it says "Couldn't find valid system superblock". I do not get either of these warnings on the ubuntu partitions.

---

### Post by Leppie on 2009-12-17
> **mikitz said:**
> Dell Optiplex 755

Do you have dell angel installed in windows? this application seems to be messing up grub2.
reinstalling grub and removing the bootable flag from the windows partition should resolve it, otherwise you can use the windows boot loader to chainload into grub.

---

### Post by Leppie on 2009-12-17
install ntfsprogs:
```
$sudo apt-get install ntfsprogs
```

check the disk(s) on errors:
```
$sudo ntfsfix /dev/sdX  ##replace sdX with the concerning partition(s)
```

---

### Post by mikitz on 2009-12-17
Ok, removing the boot flag from the Win7 partition didn't do anything different. I will now attempt to use Win7 boot loader to chainload grub. I'll report back with results. Thanks for the tips!

---

### Post by Leppie on 2009-12-17
> **mikitz said:**
> Ok, removing the boot flag from the Win7 partition didn't do anything different.

did you reinstall grub first?
```
$sudo grub-install --recheck /dev/sda
```

---

### Post by mikitz on 2009-12-17
Yes, still getting the problem. Next step is to use Windows boot loader and chainload grub I guess. Just looking into that now.. any suggestions? Win7 is definitely doing something to grub2 that is making it unusable!

---

### Post by Leppie on 2009-12-17
try this:
```
1. Fix the GRUB 2 installation
2. Back up your Ubuntu partition, if you want/need to.
3. Boot Vista 
4. Download EasyBCD: http://neosmart.net/dl.php?id=1. Install it.
5. Run EasyBCD and click the "Manage Bootloader" button. Click on the "Reinstall Vista Bootloader" radio button and then on the "Write MBR" button. 
6. Boot from the liveCD (or USB, or whatever) and work your way to the Partition screen. Choose the "configure partitions manually" radio button.
7. Format the Ubuntu Partition in ext3. 
8. Continue until the last screen (step 7 of 7) and STOP. In the lower right corner you will see a button labeled "Advanced...". Click it.
9. Change the bootloader location so that it gets installed into the Ubuntu partition. 
10. Reboot. You still won't be able to boot into Karmic, so go right ahead and load Vista. 
11. Open EasyBCD and click on the "Add/Remove Entries" button.
12. Click on the "Linux" tab, pick the partition, tell EasyBCD your dealing with GRUB and give it a name. Then click on "Add Entry"
13. Reboot and enjoy.
```

---

### Post by mikitz on 2009-12-17
All is well! Thanks so much Leppie. You saved me A LOT of time.

The steps posted worked well (originally: [http://ubuntuforums.org/archive/index.php/t-1341624.html](http://ubuntuforums.org/archive/index.php/t-1341624.html))

Only 2 differences - I had an issue with installing EasyBCD in Windows 7: it failed saying "EasyBCD has detected that your BCD boot data and MBR are either not from the latest version or don't yet exist"

The problem was that C: was not set as the active partition!
To fix this, I had to right click on "Computer" from the start menu, select "Manage", select "Disk Management" under "Storage" and right click on C: and select "Mark Partition as Active" (Everything in Windows is done with your clicker finger .. blech)

Now EasyBCD installs and I am able to follow steps 5&6.
However I am not doing steps 7-8 reinstalling Ubuntu, instead I am installing grub on the boot sector of the current ubuntu partition.

Then follow step 9 onwards...

---

### Post by Leppie on 2009-12-17
> **mikitz said:**
> All is well! Thanks so much Leppie. You saved me A LOT of time.

Now EasyBCD installs and I am able to follow steps 5&6.
However I am not doing steps 7-8 reinstalling Ubuntu, instead I am installing grub on the boot sector of the current ubuntu partition.

Then follow step 9 onwards...

glad everything seems to work out well. hopefully you've not yet given up on ubuntu ;)

use easybcd to set windows boot manager to chainload grub one you've installed grub onto the linux partition.

---

### Post by mikitz on 2009-12-17
Ok whoops, I spoke too soon... The Windows boot loader goes into Windows okay. However when I select Ubuntu it goes to the grub command line.. and then it gets worse! When I try to do the command 
root (hd0,6)
it tells me:
Unrecognized partition table for drive 80. Please rebuild it using a Microsoft-compatible FDISK tool (err-22). Current C/H/S=16383/18/63

BUT /dev/sda6 is a linux partition with Karmic on it! I am very confused now... Any ideas? Oh and it says the same message for root (hd0,0) thru (hd0,6)

---

### Post by Leppie on 2009-12-17
boot from the ubuntu live cd and post the output of this command:
```
$sudo fdisk -l
```

---

### Post by mikitz on 2009-12-18
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13        5623    45062860    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            5623        9727    32958360    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5            9552        9727     1402554   82  Linux swap / Solaris
/dev/sda6            5623        9552    31555788   83  Linux

Partition table entries are not in disk order

```

I have already performed ntfsfix on both NTFS partitions as Leppie suggested earlier..

---

### Post by mikitz on 2009-12-18
Ok, from the livecd, I am using testdisk in an attempt to fix the partitions. Have to enable universe repository first 
(from System->Administration->Software Sources in the "Ubuntu Software" tab, check the "universe" repository and click "Close" and then "Reload")
from command line run
```
sudo apt-get install testdisk
```
will post back results

EDIT: I let testdisk redo the mbr and it broke windows. I think something was wrong with the way it was originally installed. We are going to start over with a fresh install and try the steps listed again.

---

### Post by mikitz on 2010-02-28
Just to update, we had to get the lab working ASAP so we ended up installing Ubuntu using Wubi and everything worked out. Seems like grub2 and Win7 don't get along.

---

### Post by perham on 2010-03-06
I had the same issue. I've downgraded to grub legacy (0.97) and it works without any problems. all you need to do is to remove all grub2 files, copy grub files into /boot/grub, create a new menu.lst and setup grub.

to setup grub, just run grub in a terminal, and run these commands:

root (hdX,Y) // <-- your ubuntu partition
setup (hdX,Y) // <-- if you want to install it in your partition. 
OR
setup (hdX) // <-- if you want to install it in the mbr.

done.

you can download grub legacy files from here: [ftp://alpha.gnu.org/gnu/grub/grub-0.97-i386-pc.tar.gz](ftp://alpha.gnu.org/gnu/grub/grub-0.97-i386-pc.tar.gz)

---

