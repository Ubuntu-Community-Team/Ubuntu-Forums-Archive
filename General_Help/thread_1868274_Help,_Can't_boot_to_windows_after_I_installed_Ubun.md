---
title: "Help, Can't boot to windows after I installed Ubuntu"
date: 2011-10-24
forum: General Help
---

### Post by Sqrly on 2011-10-24
I downloaded Ubuntu 11.10 64 bit, I downloaded the tool to make a USB installer.

I installed it from the USB choosing the side by side with windows 7 option and moved the slider to let linux use 150gb of HD space.

When I reboot my PC if I choose windows 7 on the boot menu I get the message "partition not found". 

How do I fix this so I can boot to windows 7?

Please note: This is the first time I've ever even seen linux so I"m completely ignorant of the simplest things about this OS.

I do know dos and windows pretty well.

---

### Post by OneXero on 2011-10-24
Try using a windows recovery disk.

---

### Post by Sqrly on 2011-10-24
I don't have a "Recovery Disk".

I have a "Windows 7 x64 OEM DVD".

I tried booting off it and running recovery tools. It can't find any start up errors.

---

### Post by OneXero on 2011-10-24
> **Sqrly said:**
> I don't have a "Recovery Disk".

I have a "Windows 7 x64 OEM DVD".

I tried booting off it and running recovery tools. It can't find any start up errors.

Yeah, the install disks work as a "recovery disk," so that's just as good. When it detects your installation it finds no errors eh? And when you boot up it says No such partition?

Have you tried going into command line on the start-up repair and running bootrec.exe /fixmbr?

I've broken linux before, but recovered windows doing this, then I just reinstall linux and that fixes both...

---

### Post by TerryP on 2011-10-24
Sounds more like a boot-loader issue. I rather doubt anything is wrong with Win7 if Ubuntu was installed using a default side by side installation. You can try updating Grub2 from within Ubuntu. Also, you could use a utility called SuperGrubDisk. It works about 90% of the time. Boot your PC from it, scan the drive for all Operating Systems, select Win7 and boot. That can give you some piece of mind that your Win installation is OK before troubleshooting the Grub Boot-loader. There are probably others here that are more experienced in walking you through the details of fixing Grub.

Using bootrec.exe /fixmbr is a good start to recovering the original Windows MBR. Good idea. It's much easier to reinstall Ubuntu than Windows.

---

### Post by Sqrly on 2011-10-24
Well,

I tried the bootrec/FixMbr and now the pc won't boot at all. On my kids laptop atm.

---

### Post by OneXero on 2011-10-24
> **Sqrly said:**
> Well,

I tried the bootrec/FixMbr and now the pc won't boot at all. On my kids laptop atm.

Yeah sorry, I hope you know my advice may not always work and comes with a big disclaimer: "It has worked for me, may not work for you."

What do you mean "Won't boot at all" - not to any kind of disk? Have you tried USB / CD of linux recovery or a linux distro?

---

### Post by TerryP on 2011-10-24
You could write a new MBR using TestDisk.

[http://forums.techguy.org/all-other-software/917915-testdisk-restore-mbr.html](http://forums.techguy.org/all-other-software/917915-testdisk-restore-mbr.html)

---

### Post by SwitchDK on 2011-10-24
Hi Sqrly,

Sorry to hear that your machine is almost "comletely" broken now. 

My suggestion, which also looks like has been suggested previously in the thread, is to rebuild the Master Boot Record (MBR). Once that is working then Windows will boot. When you then have access to Windows again you can try installing Ubuntu again.

In the past to fix the MBR I have used this guide:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I hope it helps you too. Let us know how you get on.

---

