---
title: "ubuntu boot problem - wubi"
date: 2012-10-14
forum: General Help
---

### Post by cocoza4 on 2012-10-14
I'm using Ubuntu 12.04 with Windows 7 (Wubi installation)
I encounter booting problem to Ubuntu many times (after choosing to boot to Ubuntu, it appears black screen).
I try to repair by boot-repair. It worked sometimes.
I have no idea how to fix it (is it about my hdd?)

Here's an URL:
[http://paste.ubuntu.com/1279444/](http://paste.ubuntu.com/1279444/)

Thanks in advance

---

### Post by oldfred on 2012-10-14
I do not know wubi, and only a few here do. Added wubi to your title to show it is a wubi issue.

Normally Boot-Repair will only fix boot issues. But it sounds like you are booting into the Windows boot menu ok. After that do you get a grub menu? Not sure with wubi if you still get the grub menu or not as it may just continue booting. Then it may be a video issue.

What video card do you have? Does liveCD run ok?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by cocoza4 on 2012-10-14
i do get grub menu
my video card is NVIDIA GeForce 310M
and i can run liveCD

i tried to run chkdsk /r to check the file system but it stucked at 12%

---

### Post by oldfred on 2012-10-14
At grub menu you can try the nomodeset if chkdsk ever ends.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by evilsoup on 2012-10-14
How long have you had Wubi installed?

---

### Post by cocoza4 on 2012-10-14
I tried nomodeset but it didn't work.
I still can't boot to Ubuntu.

I have installed Wubi for 1 week.

---

### Post by Karlchen on 2012-10-14
Hello, cocoza4.
> **cocoza4 said:**
> i do get grub menu
my video card is NVIDIA GeForce 310M
and i can run liveCD
i tried to run chkdsk /r to check the file system but it stucked at 12%Those posters identifiying your video card as the reason why you get a black screen only when trying to boot to Ubuntu may be right.

Yet, you may have another nasty problem as well:
You installed Ubuntu with the help of Wubi. Wubi creates a large file named root.disk on the Windows NTFS partition, folder \ubuntu\disks.
This root.disk holds the Ubuntu filesystem. This will be ext2, ext3 or ext4. (Most likely ext4)

Your Wubi Ubuntu can only be started provided the underlying NTFS filesystem is clean. 
But you report > i tried to run chkdsk /r to check the file system but it stucked at 12% This suggests that the NTFS filesystem and/or your harddisk has got a serious problem.
If this is true then this problem will prevent your Ubuntu from starting up as well.
So it is essential to make sure that the Windows drive which holds your Ubuntu Wubi root.disk works properly.

Next take care of the potential graphics driver problem as suggested.

Kind regards,
Karl
--
[SIZE=1]P.S.:
I have been running Windows 7 on NTFS partitions for  about 2.5 years now. I have been running Ubuntu 10.04(.4) for the past 2 1/4 years as a Wubi installation living on the D: drive of said Windows 7 installation. Neither of the 2 Windows 7 NTFS partitions has ever experienced any serious filesystem problem, hence neither has my Wubi installation.
[/SIZE]

---

### Post by cocoza4 on 2012-10-14
I tried to chkdsk /r again and it works well. My drive is clean (it's not stuck at 12% anymore i thought it was stuck but actually it wasn't). 

I think it's because of my graphics card (NVIDIA GeForce 310M)

does anybody know how to fix it?

---

### Post by Karlchen on 2012-10-16
Hello, cocoza4.

Good to know that your booting problems are definitely not caused by NTFS filesystem problems. :)

Googled around a bit about Ubuntu and your particular Nvidia graphics card. - Two of my machines have got Nvidia cards as well, but different types. No black screen problem here.

Came across **[this report]("http://www.sanafapech.net/2011/04/geforce-310m-330m-400m-etc-con-linux.html")**: It suggests that if you have not yet installed the proprietary NVidea drivers, but if you are still using the nouveau driver which comes with Ubuntu 12.04 out of the box, then on next reboot you should press E to edit the boot commandline and replace **quiet nosplash** by **nouveau.modeset=0** and press **<F10>** to boot using the modified commandline.
[SIZE=1](Forget about editing /boot/grub/grub.conf. First of all the file is called /boot/grub/grub.cfg on recenet Grub versions. Directly editing this file is not recommended anyway, because the next run of "sudo update-grub" will overwrite any manual changes to it. Finally and most important for you, /boot/grub/grub.cfg is not present on Wubi installations. )

[SIZE=2]Provided you succeed in booting your Wubi Ubuntu12.04 this way, and provided you have not done so, you should install the proprietary NVidia driver (nvidia-current) by going to System Settings => Additional Drivers.

[SIZE=2]Provided this works fine[SIZE=2], reboot again. Press E again and remove the string **nouveau.modeset=0**[SIZE=2] from the commandline [SIZE=2]and press [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][SIZE=1][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2]**<F10>** again to boot using the modified [SIZE=2]commandline.

[SIZE=2]HTH,
[SIZE=2]Karl
[SIZE=2]--
[SIZE=2]P.S.:
[SIZE=2]To the best of my knowledge, [**Boot Repair**](http://ubuntuforums.org/showpost.php?p=12295234&postcount=1) is not meant for Wubi installations. The reason is that on Wubi systems, the Windows bootmgr is still in place and the only bootmgr. The Wind[SIZE=2]ows bootmgr cha[SIZE=2]in loads [SIZE=2]the Linux Grub boot manager [SIZE=2]with the help of [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]the file wubildr.
[SIZE=2]Boot Repair is meant to fix a defective Grub configuration where Grub is sitting in /dev/sda[SIZE=2], i.e. in the master boot record of the harddisk. On Wubi systems Grub[SIZE=2], however[SIZE=2], must never be installed into the harddisk MBR.

[/SIZE][/SIZE]
[/SIZE][/SIZE]

---

### Post by oldfred on 2012-10-16
With wubi all Boot-Repair should do is reinstall a Windows like boot loader - syslinux into the MBR to boot Windows.

Then you are into video issues or needing other boot parameters depending on system.

---

