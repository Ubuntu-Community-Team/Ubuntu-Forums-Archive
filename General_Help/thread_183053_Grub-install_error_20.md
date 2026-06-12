---
title: "Grub-install error 20"
date: 2006-05-27
forum: General Help
---

### Post by leohart on 2006-05-27
I have recently reinstalled Windows and GRUB is gone. 

In order to boot back into Linux, I have to install GRUB so I followed the instructions on ubuntuguide.org and boot into my Ubuntu CD Rescue mode.

I loaded the right / then I chose Reinstall GRUB. 

The problem is, it doesn't matter what I choose (/dev/hda1 , /dev/sda1 ,...), grub-install return error 20.

I have been searching online for a while and find no information about error 20. Does anyone has any suggestion to my problem?

My Ubuntu installation is in sdb (1,3,5) while my Windows first boot disk is on /dev/sda1

---

### Post by lha on 2006-05-29
See [http://ubuntuforums.org/showthread.php?t=76652]("http://ubuntuforums.org/showthread.php?t=76652"). If you installed Grub on sda1, you have overwritten Windows' boot loader, so you have to repair it, too. (Use Windows cd to do that.)

---

### Post by oli888 on 2006-05-29
If you can't solve it with the forum thread, you might want to try to install LILO as your boot loader. I'm quite new to Linux so I don't know the differences.

Oli

---

### Post by leohart on 2006-05-29
I really prefer GRUB over LILO so installing LILO is not an option. (just personal preference)

I think I will try the intructions in the post lha pointed to. 

But before messing anything up I have backed up my Linux home folder using Explorer2fs.

```
If you installed Grub on sda1, you have overwritten Windows' boot loader, so you have to repair it, too. (Use Windows cd to do that.)
```
Regarding this, I thought that installing GRUB on MBR of my first drive (sda1) is necessary to boot up GRUB.

---

### Post by Irony on 2006-05-29
Boot from the install ubuntu CD (doesn't matter which version)  and at the boot prompt type;

[PHP]rescue[/PHP]

Go to the mount point (where ubuntu is located, say sdb1);

[PHP]dev/disc/disc1/part1[/PHP]

At the sh-3.00# prompt type (installing it to MBR);

[PHP]grub-install /dev/sda[/PHP]

Note don't put a number after sda.

After being returned to the prompt, do;

[PHP]#umount /dev/sdb1
#reboot[/PHP]

Thus grub is installed to the MBR and grub points to the ubuntu in sdb1.

If it doesn't work you can always try again, trying something slightly different, as it only takes a few minutes.

---

### Post by lha on 2006-05-29
[QUOTE=leohart]I really prefer GRUB over LILO so installing LILO is not an option. (just personal preference)

I think I will try the intructions in the post lha pointed to. 

But before messing anything up I have backed up my Linux home folder using Explorer2fs.

```
If you installed Grub on sda1, you have overwritten Windows' boot loader, so you have to repair it, too. (Use Windows cd to do that.)
```
Regarding this, I thought that installing GRUB on MBR of my first drive (sda1) is necessary to boot up GRUB.[/QUOTE]
Yes, you need to have grub on sda (primary master's mbr) but you need to have Windows' boot code on sda**1** (the boot sector of first partition on primary master) to be able to boot Windows.

---

