---
title: "New Xubuntu install and now cannot boot into XP"
date: 2009-07-30
forum: General Help
---

### Post by hattersluck on 2009-07-30
So, looks like I am the lucky fellow who always has the lucky boot problems.

I decided to switch back to a dual boot system after losing both drives to a crash, thankfully I had a back up of my work XP system. After putting my XP install back on and running fine I went back and installed Xubuntu without a hitch.

I restarted my system and look, no XP in the GRUB menu. I looked around and even after manually trying to add it I get NTLDR is missing, restart.

I went ahead then and just switched the boot order to force it to boot from the XP drive, seeing if I could just do it that way, nope still NTLDR problem and even after FIXBOOT and FIXMBR problem still happens.

so I've come to you ubuntu community who knows all, to wonder if it's possible to add XP to the GRUB and not have to worry about re-installing which I had done before a couple years back when this happened the first time. Took about an hour of re-installing and re-arranging install orders before it worked right..

What commands do you folks need me to do to output you the proper information to assist me in fixing my problem?

---

### Post by prshah on 2009-07-30
> **hattersluck said:**
> 
What commands do you folks need me to do to output you the proper information to assist me in fixing my problem?

I suspect you have wiped out the XP partition altogether. Here's a quick way to confirm: Open the terminal (Applications-Accessories-Terminal) and give the comman ```
sudo fdisk -l
```; this will list your partitions, all we need to see is if you have any FAT32 / HPFS / NTFS partitions.

If you can post back the output, someone can advise you on the specific changes to be made.

---

### Post by hattersluck on 2009-07-30
Here is the output of sudo fdisk -l

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c473c46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60045   482311431   83  Linux
/dev/sda2           60046       60801     6072570    5  Extended
/dev/sda5           60046       60801     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13171c4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24791   199133676    7  HPFS/NTFS

```

---

### Post by GenePayne on 2009-07-30
It looks like you still have a partition for your Windows XP.
Please post the contents of your grub bootloader menu. Type:
```

cat /boot/grub/menu.lst
```

---

### Post by hattersluck on 2009-07-30
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8a88b83a-3e0a-47db-a435-44555f2bdb9a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8a88b83a-3e0a-47db-a435-44555f2bdb9a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=8a88b83a-3e0a-47db-a435-44555f2bdb9a ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=8a88b83a-3e0a-47db-a435-44555f2bdb9a ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by GenePayne on 2009-07-30
It looks like your GRUB bootloader menu has no entry for Windows XP. Try adding an entry for it by adding the following to the END of your /boot/grub/menu.lst.

First, make a backup copy of your menu file:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak1
```

Next, edit your menu file:
```
sudo gedit /boot/grub/menu.lst
```

Paste the following at the very end of the file:
```
# Entry for Windows XP
title		Microsoft Windows XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

Then reboot and see if that works.

---

### Post by hattersluck on 2009-07-30
Sadly no, that does not work. All it does after selecting the Entry is go to Starting up... and then stays there.

---

### Post by merlinus on 2009-07-30
Try changing this:
title        Microsoft Windows XP
root        (hd1,0)
savedefault
makeactive
chainloader    +1

to this:

title        Microsoft Windows XP
rootnoverify        (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader    +1

---

### Post by hattersluck on 2009-07-30
Went and changed the XP entry as you suggested and it comes up with NTLDR is missing.

As XP is on a SATA Drive and xubuntu is on an IDE drive could that somehow be possibly creating this problem?

---

### Post by merlinus on 2009-07-30
Which hdd is first in boot order in bios?

However, it looks like grub found xp, but ntldr is the windows bootloader.  If missing, it could not start.

What method did you use for shrinking the xp partition when first installing linux?

Another option is to use supergrub to fix the problem:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by GenePayne on 2009-07-30
Was your system booting into XP before you installed Xubuntu? What happens if you physically disconnect your 500GB hard drive (sda), and make the other drive the master and boot from that? Does it correctly boot into XP?

---

### Post by hattersluck on 2009-07-30
Currently I have it set to the IDE drive booting first, I had switched it before to the SATA drive and got the NTLDR error. I left it as SATA, fixbooted and fixmbr the drive but still had the error so I switched back to the IDE being first.

I did not shrink any drive when I installed Linux, both are on completely separate drives.

---

### Post by hattersluck on 2009-07-30
XP was running perfectly fine before installing Xubuntu. Even when disconnecting the 500 and running the XP drive as master I get the same error. It looks like what might have happened is that when I put XP back on the 200 my 500 received the boot information, so when I installed Xubuntu on the 500 it probably wrote over XPs boot information, which shouldn't have mattered when I then went in and fixbooted and fixmbred.

Any ideas on what I can do to where I do not have to re-install and switch everything about?

---

### Post by GenePayne on 2009-07-31
OK, that's probably why the GRUB bootloader menu changes we suggested didn't work. GRUB is correctly jumping to your XP partition on the 200GB hard drive, but then windows can't boot from there.

It might be a windows problem from this point. Here is what I would try:

1. Create a windows XP boot disk. I think you usually have to already be in windows to create such a disk, but maybe you can download an .iso image of such a disk online from within Xubuntu.
2. Physically remove the 500GB drive and make the 200GB the master drive.
3. Insert the windows xp boot disk.
4. Boot your computer, and go into the windows boot disk menu. I'm not certain, but it might restore windows boot information to the 200GB partition. If not, then the rest of these steps won't work.
5. Turn off your computer, remove the windows boot disk, and reboot
6. Verify that you can boot into windows.
7. If you successfully booted into windows, turn off computer, reconnect 500GB hard drive, and make it the master drive.
8. Boot your computer, and try to boot into windows using the /boot/grub/menu.lst that was posted earlier.

---

