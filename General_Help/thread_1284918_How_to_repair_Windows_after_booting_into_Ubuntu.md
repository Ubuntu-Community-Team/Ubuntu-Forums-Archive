---
title: "How to repair Windows after booting into Ubuntu"
date: 2009-10-07
forum: General Help
---

### Post by Erazer on 2009-10-07
Hi All,

I've just now joined this forum hoping that my querries can be solved here. Hence I'm posting my questions below with a short description of the cause of trouble.

I was using Ubuntu 9.04 with Windows XP Professional, both were working fine until last week. Then Windows XP was hit by a trojan virus and it crashed. Now I am not able to boot with windows CD and I don't want to remove Ubuntu to do that. So my questions are:

1) Is there a way to repair Windows through Ubuntu? If not, then how can I keep Ubuntu and still format my windows partition?

2) Would it be advisable to make changes in grub for the purpose? If yes then how to restore grub after my work is done.

3) If both the above cases don't work then can I install and run windows applications on Wine in Ubuntu even if I remove windows completely?

---

### Post by DeBOBAHer on 2009-10-07
If you have Ubuntu CD than you can use its recovery functions. So you can reinstall windows. After that you'll be able to run restore from the Ubuntu CD-ROM and select there recover GRUB or something like that.

---

### Post by Erazer on 2009-10-07
hey friend can you explain me a little bit about how to use the recovery function. Is it the Gparted that you are talking about or its something else? please elaborate.

---

### Post by DeBOBAHer on 2009-10-07
When you boot from Ubuntu install CD-ROM it ask you about what you want to do - install, repair or boot in liveCD session. You can choose repair and then you will be able to do some things with you system. I can't now look at that menu and tell exactly what there are but if it similar to recovery mode from the boot menu of hard drive you will be able to correct you boot loader from there.
To be absolutely chore about this you can try to boot in recovery mode from the Ubuntu install CD-ROM and look what it could do and how.
Try to look this topic too:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by prshah on 2009-10-07
> **Erazer said:**
> 
1) Is there a way to repair Windows through Ubuntu? If not, then how can I keep Ubuntu and still format my windows partition?

2) Would it be advisable to make changes in grub for the purpose? If yes then how to restore grub after my work is done.

3) If both the above cases don't work then can I install and run windows applications on Wine in Ubuntu even if I remove windows completely?

You can use a number of linux antivirus utilities (such as avg, f-prot or Kaspersky [paid / 30-day trial available?] ) to repair / disinfect your Windows partitions. 

See [this post]("http://ubuntuforums.org/showpost.php?p=6228860&postcount=4") for suggestions; post back if you need more details.

==

If you plan to reinstall Windows, you will lose GRUB. To prevent this, make a copy of your bootsector (WARNING: Dangerous commands ahead). Boot into Ubuntu, open the Terminal (Applications-Accessories-Terminal) and give the command```
sudo dd if=/dev/sda of=/bootsect bs=446 count=1
``` This will create a file bootsect in / (root) that contains the GRUB bootup code. (This assumes you have only a single hard disk, on which both Ubuntu and Windows are installed). Post back with more details if this is not the case).

Also make a note of which partition contains the "/" file system; you can see this with the command ```
mount | grep " \/ " | cut -f 1 -d " "
``` The output should be (for example) "/dev/sda3" (Only the last digit may change).

You can then exit linux and install Windows. After installing Windows (be careful not to damage / overwrite linux partitions during installation), you can use a live CD to boot into Ubuntu. You will then need to open the Terminal and give the following series of commands```
sudo mount /dev/sdaX /mnt -o defaults,ro
``` (Replace /dev/sdaX with the correct partition code as gained from the previous "mount" command).

```

sudo cp /mnt/bootsect / && sudo umount /mnt && sudo dd of=/dev/sda if=/bootsect bs=446 count=1
sudo reboot

```

WARNING: THE ABOVE COMMANDS ARE EXTREMELY DANGEROUS. A single spelling or typo mistake will INSTANTLY render your data unavailable. Please be VERY VERY careful.

ADDITIONAL WARNING: It may be wise to wait for someone else's comments incase I have made a mistake in the above commands.

This will restore your GRUB as it was before installing Windows.

==

WINE does not require Windows to work, so if your application worked in WINE before, it will continue to do so, even if you cannot get your Windows to work.

==

I would really recommend that you first try using linux-based antivirus programs to "disinfect" your Windows partition.

---

### Post by philinux on 2009-10-07
> **DeBOBAHer said:**
> If you have Ubuntu CD than you can use its recovery functions. So you can reinstall windows. After that you'll be able to run restore from the Ubuntu CD-ROM and select there recover GRUB or something like that.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

There is no recovery option on the live cd. See section 3 for the options offered. Unless he means something else.

However you can use the live cd to backup any important files from windows or run a virus scan on it.

---

### Post by karlson on 2009-10-07
> **Erazer said:**
> Hi All,

I've just now joined this forum hoping that my querries can be solved here. Hence I'm posting my questions below with a short description of the cause of trouble.

I was using Ubuntu 9.04 with Windows XP Professional, both were working fine until last week. Then Windows XP was hit by a trojan virus and it crashed. Now I am not able to boot with windows CD and I don't want to remove Ubuntu to do that. So my questions are:

1) Is there a way to repair Windows through Ubuntu? If not, then how can I keep Ubuntu and still format my windows partition?

2) Would it be advisable to make changes in grub for the purpose? If yes then how to restore grub after my work is done.

3) If both the above cases don't work then can I install and run windows applications on Wine in Ubuntu even if I remove windows completely?

Something tells me that runing VMWARE or Xen through Ubuntu Primary System would be much preferred to what you're trying to do.

BTW,

What does you Windows CD boot tell you when try to boot from it?

---

### Post by Erazer on 2009-10-08
Well thanks to all of you for giving me advices......yesterday I ran a scan on my HDD from the BIOS menu and after that my Windows CD boots to the setup menu......but I really don't like using windows any more as every now and then it crashes.....but there are certain softwares that are available only for windows so its just that I have to use it unwillingly......anyways I'll try the suggestions from you all and then get back to you informing whether they worked for me or not........I hope as prshah said I should first try to disinfect my windows before working out other steps.....so I'll try that first.

---

### Post by Erazer on 2009-10-09
Hi friends,

Thanks prshah ur advice worked.
I first installed Bitdefender in ubuntu and then scanned Windows drive. It caught some 1300 files infected with virus, but that didn't help much as windows was very badly effected.
Then I followed the steps you told about backing up grub and the restoring it running those commands. That worked perfectly and now my Windows is back and working fine with Ubuntu.

Thanks a tonn...:)

---

