---
title: "recover deleted ntfs partition"
date: 2010-05-30
forum: General Help
---

### Post by amsonia on 2010-05-30
First off, I hate asking this question, but it sometimes even Linux nerds face these sort of issues.  And the fact that I'm asking here says volumes about why Linux is better than Windows.  Using Windows 7, I accidentally deleted a Windows XP partition.  It's really no big deal, but there are important files on the Windows XP partition and it would be cool to be able to boot back into the Windows XP partition for some reason (not really sure exactly what that reason is, but trust me there is some reason--OS archeology maybe).  How do I can I undelete the Windows XP partition?  

Thanks for answering this question!  And I will perform some appropriate penance like buying the snacks for my next Linux User Group meeting.

---

### Post by Ozymandias_117 on 2010-05-30
Dunno about a complete undelete, but if you boot into windows 7 and use Piriform's Recuva: [http://www.piriform.com/recuva]("http://www.piriform.com/recuva") You should be able to get your important files back.

---

### Post by finlost on 2010-05-30
I will ask the obvious....Does booting with a Live CD allow you to see the deleted partition?

---

### Post by john newbuntu on 2010-05-30
Look into the "testdisk" utility.  It could help you recover your partition:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)
[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

---

### Post by bakegoodz on 2010-05-30
testdisk will restore deleted partitions, if that all you done. If you reformatted you have to use a data scraper like photorec, it will recognize types of files, but say goodbye to your folder and filenames. If you need a live CD with recovery tools SystemrescueCD is good one [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
If you restore that partition, I would run chkdsk after.

---

### Post by BoneKracker on 2010-05-30
++ on SystemRescueCD



[COLOR="White"].[/COLOR]

---

### Post by amsonia on 2010-05-31
Following the directions from Microsoft, I created a partition where the NTFS parition was, but I couldn't follow the rest of Microsoft's directions because the directions referred to programs apparently not on my PC.  Whatever!  I did not format the XP partition, and I'm utterly certain that I did format XP parition because I knew it would be the end of easy hope.  Linux (fdisk) now thinks that the NTFS partition is a FAT16 partition.  testdisk seems uninterested in helping me unless I'm not understanding.  

I'm going to use hexedit on the MBR and see if that is enough to get the XP pariition to boot.  Any other ideas?

---

### Post by aysiu on 2010-05-31
There's a program called GPart (not to be confused with GParted) that is supposed to restore damaged partition tables:
[http://www.brzitwa.de/mb/gpart/index.html](http://www.brzitwa.de/mb/gpart/index.html)

Not sure if that'll help or not, but Photorec certainly will help you get your files back even if you cannot restore your partition:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

### Post by formaldehyde_spoon on 2010-05-31
> **amsonia said:**
> Following the directions from Microsoft, **I created a partition where the NTFS parition was**, but I couldn't follow the rest of Microsoft's directions because the directions referred to programs apparently not on my PC.  Whatever!  I did not format the XP partition, and I'm utterly certain that I did format XP parition because I knew it would be the end of easy hope.  Linux (fdisk) now thinks that the NTFS partition is a FAT16 partition.  testdisk seems uninterested in helping me unless I'm not understanding.  

I'm going to use hexedit on the MBR and see if that is enough to get the XP pariition to boot.  Any other ideas?

That sounds like a bad idea to me.

Scrapers like photorec or scalpel will work to a limited degree, but they only find sequential data. Is there no such thing as a data recovery tool for a specific filesystem? Anyone?

---

### Post by oldfred on 2010-05-31
In system, administaration, disk utility ( at least from 9.10) it shows type and lets you change the type. My NTFS should be 07 and it shows 0x07. You may be able to change type but note that that may have risk.

---

### Post by BoneKracker on 2010-05-31
A quick google for recover ntfs partition turns up what appear to be multiple free tools for the purpose.  Here is one:
[http://www.dtidata.com/resourcecenter/freeware-data-recovery/](http://www.dtidata.com/resourcecenter/freeware-data-recovery/)

---

### Post by sonicb00m on 2010-05-31
Getdataback for NTFS has rarely ever let me down.

If you have just deleted the partition table it should restore your files pretty much perfectly.

I used it this weekend after the partition was no longer readable and I got 100% recovery rate. I've also used it in the past after various accidents.

---

### Post by Mark Phelps on 2010-05-31
> **sonicb00m said:**
> Getdataback for NTFS has rarely ever let me down.

+1 -- best NTFS data recovery software out there.  Has worked perfectly for me, every time!

---

### Post by BoneKracker on 2010-05-31
> **Mark Phelps said:**
> +1 -- best NTFS data recovery software out there.  Has worked perfectly for me, every time!

Only $79, while supplies last.  It slices, it dices, and watch this... voila... hors d'oeuvres!  Add FAT for only $69 more!  If you recover your drives every day, that's only $2.84 a week! 
[http://www.runtime.org/data-recovery-software.htm](http://www.runtime.org/data-recovery-software.htm)

---

### Post by amsonia on 2010-06-01
[Problem solved]
I had no luck using the command line program testdisk in Linux to undelete the NTFS partition where my Windows XP was because I ran testdisk on just the NTFS partition.  I used testdisk on the whole disk (testdisk /dev/sdb) and I can now boot Windows XP.  I had no luck undeleting the NTFS partition using the Windows 7 operating system.  Experiences like this truly show the superiority of Linux!

By the way, if you opt just get the data out of the NTFS, you can use GetDataBack to determine what you to get back, and then use photorec to get it back.  photorec tends to be bring multiple copies of files, so I'd run fdupes -rdN to get rid of them before searching to find the files you want.  The problem with photorec is it doesn't bring back the files names, as I assume GetDataBack does.  You thus have to find the files and rename them.

---

