---
title: "[Lucid] Help with re-installation..."
date: 2010-09-19
forum: General Help
---

### Post by ProcuratorIncendia on 2010-09-19
Hello people who read this...
1. I accidentally wrecked a previous Ubuntu installation so I decided to re-install via the Ubuntu disk.
Unfortunately Ubuntu doesn't let me override previous Ubuntu installations...
2. Ubuntu Maverick Meerkat is due to released in about 3 weeks. I want to install it via a clean install.
3. So can anyone tell me how to remove both Ubuntu partitions safely. I am currently running WinVista with Ubuntu Lucid Lynx.
I know I have to use something like [this]("http://download.cnet.com/MbrFix/3000-2094_4-10485990.html") to erase GRUB2. Can anyone give me a good tutorial?

---

### Post by wilee-nilee on 2010-09-19
> **ProcuratorIncendia said:**
> Hello people who read this...
1. I accidentally wrecked a previous Ubuntu installation so I decided to re-install via the Ubuntu disk.
Unfortunately Ubuntu doesn't let me override previous Ubuntu installations...
2. Ubuntu Maverick Meerkat is due to released in about 3 weeks. I want to install it via a clean install.
3. So can anyone tell me how to remove both Ubuntu partitions safely. I am currently running WinVista with Ubuntu Lucid Lynx.
I know I have to use something like [this]("http://download.cnet.com/MbrFix/3000-2094_4-10485990.html") to erase GRUB2. Can anyone give me a good tutorial?

There is a program on the live Ubuntu cd called gparted, this is what you would use to remove and make partitions. Always do these things from a live cd. In order to remove the Ubuntu give us a screenshot of gparted first.

Reloading the mbr for Vista would be best done with a Vista install disc or this recovery cd here is a link.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Here are the instructions to reload the mbr with the MS bootloader, notice the link to the W7 forums for help on booting to the command line from the cd or a vista install dvd. You would only have to run the command in bold to do this.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

