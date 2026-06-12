---
title: "Boot Manager missing after uninstalling UBUNTU"
date: 2011-10-14
forum: General Help
---

### Post by midamah1 on 2011-10-14
Hello,

I followed a couple of websites that said that I could install the MBR through Ubtunu(I did that before uninstalling Ubuntu) so when I actually uninstalled Ubuntu using the Ubuntu remix (os uninstalling) feature, I was surprised when I restarted my computer and got the message that the "MBR is missing" and "Boot manager" was missing. 

Not sure if this helps, but when I first installed Ubuntu, I did a strictly clean install and got rid of my windows xp. I have the recovery disc for windows xp, but nothing seems to be working.

Please help, thank you

---

### Post by ibutho on 2011-10-14
I can't figure out exactly what you are saying happened, but if you removed Linux and need to fix your MBR try the suggestions [here]("http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/").

---

### Post by TheDesertDragon on 2011-10-14
> **midamah1 said:**
> Hello,

I followed a couple of websites that said that I could install the MBR through Ubtunu(I did that before uninstalling Ubuntu) so when I actually uninstalled Ubuntu using the Ubuntu remix (os uninstalling) feature, I was surprised when I restarted my computer and got the message that the "MBR is missing" and "Boot manager" was missing. 

Not sure if this helps, but when I first installed Ubuntu, I did a strictly clean install and got rid of my windows xp. I have the recovery disc for windows xp, but nothing seems to be working.

Please help, thank you

This happens because you removed Windows and install Ubuntu, then removed Ubuntu. The MBR sits in the start of your drive and points towards which partition to boot from. When you installed Ubuntu, Ubuntu pointed the MBR to it to boot into GRUB. It still does, but Ubuntu is missing!

There is only 1 possible solution: Find a Windows (or whatever you want to use) disc, and boot from it, then install the OS. Another option is reinstalling Ubuntu, then installing the other OS, removing access to the Ubuntu partition. Then remove Ubuntu from the partition manager of the OS of your choice.

---

### Post by midamah1 on 2011-10-14
> **TheDesertDragon said:**
> This happens because you removed Windows and install Ubuntu, then removed Ubuntu. The MBR sits in the start of your drive and points towards which partition to boot from. When you installed Ubuntu, Ubuntu pointed the MBR to it to boot into GRUB. It still does, but Ubuntu is missing!

There is only 1 possible solution: Find a Windows (or whatever you want to use) disc, and boot from it, then install the OS. Another option is reinstalling Ubuntu, then installing the other OS, removing access to the Ubuntu partition. Then remove Ubuntu from the partition manager of the OS of your choice.

Thank you, you understood what I was saying.

Even with the system disk, I'm still getting that the bootmanager is missing, but when I put in the ubuntu cd it loads without a problem.

When I had ubuntu before I installed it, I tried to load the windows disk, but nothing would come up. So if I had to go with your other option which was to reinstall ubuntu and then install windows, how would I install windows if the disk wasn't picking up before? (i've used several system disks for windows).

---

### Post by drs305 on 2011-10-14
There is one more thing you can try with the Ubuntu CD. *IF* the Windows boot files are intact and all you need is to fix the MBR, you can boot an Ubuntu CD and run some commands from a terminal.
```

sudo apt-get install lilo
sudo lilo -M /dev/sd**a **mbr
```
It will tell you to run the lilo configuration commands. Don't - just the two above and reboot to see if Windows is now usable.

This assumes your Windows installation:
[LIST]
[*]is on sd**a** (change the command if it isn't)
[*]The boot flag is set on your Windows boot partition.
[*]The boot files are complete and all you need is for the MBR to find them.
[/LIST]

---

### Post by midamah1 on 2011-10-14
> **drs305 said:**
> There is one more thing you can try with the Ubuntu CD. *IF* the Windows boot files are intact and all you need is to fix the MBR, you can boot an Ubuntu CD and run some commands from a terminal.
```

sudo apt-get install lilo
sudo lilo -M /dev/sd**a **mbr
```It will tell you to run the lilo configuration commands. Don't - just the two above and reboot to see if Windows is now usable.

This assumes your Windows installation:
[LIST]
[*]is on sd**a** (change the command if it isn't)
[*]The boot flag is set on your Windows boot partition.
[*]The boot files are complete and all you need is for the MBR to find them.
[/LIST]


I just tried that, (thank you) but unfortunately it says the BOOTMGR is missing (still) so I guess something is really wrong? >_<

---

### Post by midamah1 on 2011-10-14
Would it be a good idea to delete the ubuntu partitions and resize my windows partition? I'm wondering if that would make any kind of difference.

oh not sure if it means anything, but I no longer see the MBR missing, just Bootmgr missing, now.

---

### Post by drs305 on 2011-10-14
> **midamah1 said:**
> Would it be a good idea to delete the ubuntu partitions and resize my windows partition? I'm wondering if that would make any kind of difference.

I think I misunderstood your situation. You never reinstalled Windows after you removed it? If that is the case, you have no OS on your system. 

The Ubuntu CD will boot because it has it's own boot files and OS on the CD. It is self-contained and doesn't need the MBR of your hard drive.

Resizing your partitions will not help in this matter.* Your choices are to get a working Windows disk or reinstall another OS. Doing the latter probably isn't going to help you install Windows.

* The one thing that resizing helps with is when the BIOS only sees 137GB of the drive. This sometimes happens on older BIOS's and rarely on newer ones. If the drive size is reported as 137GB in the BIOS, you should install Ubuntu in a partition which does not go outside the first 137GB of the drive to ensure it will find all the boot files.

---

### Post by midamah1 on 2011-10-14
> **drs305 said:**
> I think I misunderstood your situation. You never reinstalled Windows after you removed it? If that is the case, you have no OS on your system. 

The Ubuntu CD will boot because it has it's own boot files and OS on the CD. It is self-contained and doesn't need the MBR of your hard drive.

Resizing your partitions will not help in this matter.* Your choices are to get a working Windows disk or reinstall another OS. Doing the latter probably isn't going to help you install Windows.

* The one thing that resizing helps with is when the BIOS only sees 137GB of the drive. This sometimes happens on older BIOS's and rarely on newer ones. If the drive size is reported as 137GB in the BIOS, you should install Ubuntu in a partition which does not go outside the first 137GB of the drive to ensure it will find all the boot files.


Would it be a good idea (if I had nothing to lose on the computer) to use something called DBAN and just wipe the whole hard drive clean? I'm getting desperate in my attempts of fixing the issue.

---

### Post by drs305 on 2011-10-15
> **midamah1 said:**
> Would it be a good idea (if I had nothing to lose on the computer) to use something called DBAN and just wipe the whole hard drive clean? I'm getting desperate in my attempts of fixing the issue.

You probably don't even have to wipe the drive unless you really want to start from scratch. For most OS's, the partition is going to be reformatted during the installation process and new information will overwrite the MBR anyway. If there are disk problems then completely wiping the drive may provide some marginally increased chance of correcting things. I'm not familiar with DBAN.

---

### Post by midamah1 on 2011-10-15
> **drs305 said:**
> You probably don't even have to wipe the drive unless you really want to start from scratch. For most OS's, the partition is going to be reformatted during the installation process and new information will overwrite the MBR anyway. If there are disk problems then completely wiping the drive may provide some marginally increased chance of correcting things. I'm not familiar with DBAN.

Thank you! I appreciate your help!

---

