---
title: "External hard drive"
date: 2011-11-08
forum: General Help
---

### Post by Redfox814 on 2011-11-08
Hi, I'm new here. I have ubuntu 10.something and I have an external hard drive that crashed. It doesn't mount but when I go to partition manager, it's there but I can't format it or change the volume. The current volume is Fat32(I think) and it's a 1.5tb and Omega is the brand. Anyone wanna help me?

---

### Post by oldfred on 2011-11-08
Welcome to the forums.

If it is FAT32 you need to run chkdsk from a Windows repairCD. Understand that FAT has no journal and recovery is less likely without one, but chkdsk is supposed to work. But without journal it also takes a lot longer. FAT is fine for small devices like flash drives & cards, but large drives, it really should not be used. I think vendors use FAT just because it works for all systems. NTFS is better for Windows & Linux compatibility. 

Plan on chkdsk taking many hours. And with chkdsk one pass does not fix everything. You have to rerun it until there are no errors.

Ubuntu or gparted will not use a drive/partition that has corruption/chkdsk flag set to prevent further damage that then chkdsk may not fix.

Other things you might try, but everything you do can cause further damage. Many suggest making a image copy and working on that if the data is valuable.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by Redfox814 on 2011-11-08
so what exactly is chdsk, a program or an iso or is it part of the Windows OS cd?

---

### Post by bluexrider on 2011-11-08
It was stated in the first sentence from oldfred

Re-read the response. The advise is that you do the repair with a windows repair CD.

Use your original windows installation CD 

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by Redfox814 on 2011-11-08
lol I am stupid 
I tried that. I put in the Win7 cd and it said that I needed device drivers to continue and when I put in the WinXp cd, it said that turn off computer to prevent damage

---

### Post by Redfox814 on 2011-11-08
I'm too lazy to find drivers for Win7

---

### Post by oldfred on 2011-11-08
If you do not have any Windows installed it will say that as it cannot find an active partition. Does it let you get to the repair console and can you then run chkdsk?

The drivers issue with XP may be because you have changed to AHCI in BIOS which Windows 7 should automatically work with but XP needs drivers.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:

chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors

---

