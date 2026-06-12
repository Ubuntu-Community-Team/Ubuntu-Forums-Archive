---
title: "GRUB Error 22"
date: 2009-08-05
forum: General Help
---

### Post by Elyem on 2009-08-05
Hey guys I found some threads on this topic but they either didn't work or I didn't know how to make them work. Here is the Scenario: A while back a buddy installed Ubuntu on my old laptop running Windows XP Media Center Edition. Today I was uninstalling that partition and downloading a program to reintegrate that disk space back into XP when the old laptop just suddenly died. I powered it back up to the error "GRUB error 22". I have the original Ubuntu disk and a windows bootdisk from Bootdisk.com. Feels like I have all the ducks but need some help getting them in a row. I'd like to remove the partition and restore XP to factory. I've found other threads on Linuxquestions.com but like I said for some reason they're not panning out. Any help would be great I think I've reached my Google limit. Thanks in advance.

---

### Post by prshah on 2009-08-05
> **Elyem said:**
> I powered it back up to the error "GRUB error 22".

I'd like to remove the partition and restore XP to factory. 

Use either one of your bootdisks to start the laptop.

To boot off the bootdisk, you need to make changes to the BIOS.

Usually, to enter the BIOS, you will press "del" or "f2" or "f10".. it varies from model to model.

If you reach the GRUB (error) screen, you have missed your chance. Try again.

In the BIOS, look for an option to set "boot" devices, and set the CDROM to be booted first. More exact details are not possible since the exact setup varies from BIOS to BIOS, laptop to laptop. More specific advice can be given if you can take a picture of the BIOS screen and post it here.

---

### Post by gradinaruvasile on 2009-08-05
From

[http://www.gnu.org/software/grub/manual/grub.html#Stage1-errors]("http://www.gnu.org/software/grub/manual/grub.html#Stage1-errors")


22 : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

---

### Post by Elyem on 2009-08-05
> **prshah said:**
> Use either one of your bootdisks to start the laptop.

To boot off the bootdisk, you need to make changes to the BIOS.

Usually, to enter the BIOS, you will press "del" or "f2" or "f10".. it varies from model to model.

If you reach the GRUB (error) screen, you have missed your chance. Try again.

In the BIOS, look for an option to set "boot" devices, and set the CDROM to be booted first. More exact details are not possible since the exact setup varies from BIOS to BIOS, laptop to laptop. More specific advice can be given if you can take a picture of the BIOS screen and post it here.


I've already set BIOS to read off of the CD drive. If I use the Ubuntu boot cd I can load it just fine, If I use the Windows XP Bootdisk from bootdisk.com I end at a DOS screen with A:/>  . Any advice from this point on would be appreciated. Again I'd like to get into Windows not Ubuntu.

---

### Post by Elyem on 2009-08-05
I also followed the prompts on this thread [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to see if I restored GRUB I would be able to access XP and continue the unpartitioning but when I got to the command "find /boot/grub/stage1" it gave me an Error 15: File not found.

---

### Post by Ranko95 on 2009-08-05
The same thing happened to me a while ago. I just reinstalled ubuntu and wiped windows cause it sucked :)

---

### Post by rob2uk on 2009-08-05
Don't use an XP boot disk, use the XP CD and boot from that.

When it gives you the option, choose the recovery console option- **not the 'automated system recovery'**.

From the recovery console, try the following:

```
fixboot
```

Then:

```
fixmbr
```

This replaces GRUB with the standard XP bootloader.

---

### Post by Elyem on 2009-08-05
> **rob2uk said:**
> Don't use an XP boot disk, use the XP CD and boot from that.

When it gives you the option, choose the recovery console option- **not the 'automated system recovery'**.

From the recovery console, try the following:

```
fixboot
```

Then:

```
fixmbr
```

This replaces GRUB with the standard XP bootloader.

Unfortunitley I followed the advice of another user and now it says "missing operating system" on startup. I used a supergrubdisk and at the main menu the only operating system to select is "First Kernel and Initrd". Does this mean XP is lost or can I still recover the OS without having to buy a new Windows XP OS?

---

