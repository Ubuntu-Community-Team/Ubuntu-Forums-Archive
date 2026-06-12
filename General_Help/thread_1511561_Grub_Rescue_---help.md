---
title: "Grub Rescue ---help"
date: 2010-06-17
forum: General Help
---

### Post by ThunddeR on 2010-06-17
I had windows 7 installed on my comp..
I have been using ubuntu . One day i thot of using Kubuntu. Now after installing Kubuntu i dint like it ,so i formatted the drive on which i installed it using acronis disk director.Now after restarting my comp the grub loads and since there is no file it enters in a grub rescue after tht i cant do anything. I am having loads of dat on my comp which i can't afford to loose.
I tried booting using a live Kubuntu cd and installing the grub again but it doesn't help .
Now if i try reinstalling Kubuntu it shows me tht its gonna format the whole HDD.
I ma in deep trouble ,,
some body who knows exactly wht to do please help me out in this

---

### Post by ThunddeR on 2010-06-17
anyone???

---

### Post by wilee-nilee on 2010-06-17
Post the script in my sig to begin with, and follow the code tags instruction.

And do you have a install dvd or recovery disc for W7?

---

### Post by ipatfrmww on 2010-06-17
You want to revert your MBR (master boot record) to the state it was in before you installed GRUB into it. The easiest way to do this is let windows 7 rewrite it with the windows install CD. 

If you dont have one (like me) then you would have to work out what your MBR would have looked like before GRUB. To do this you either need a third party piece of software(not sure what) or you need to copy somebody else's windows MBR and change it a bit(not sure how).

Thats a really useful script to have btw. I like it.
[]("http://ubuntuforums.org/member.php?u=906928")

---

### Post by wilee-nilee on 2010-06-17
> **ipatfrmww said:**
> You want to revert your MBR (master boot record) to the state it was in before you installed GRUB into it. The easiest way to do this is let windows 7 rewrite it with the windows install CD. 

If you dont have one (like me) then you would have to work out what your MBR would have looked like before GRUB. To do this you either need a third party piece of software(not sure what) or you need to copy somebody else's windows MBR and change it a bit(not sure how).

Thats a really useful script to have btw. I like it.
[]("http://ubuntuforums.org/member.php?u=906928")

Yeah we can just reload the mbr, I'm just trying to make sure grub isn't in the MS boot by accident or other anomalies. Here is a recovery disc link if you don't have one.
[recovery](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by ThunddeR on 2010-06-17
the problem is whenever i boot from a disc either windows or kubuntu it shows me tht its gonna format whole hdd but syill it has all data

---

### Post by wilee-nilee on 2010-06-17
> **ThunddeR said:**
> the problem is whenever i boot from a disc either windows or kubuntu it shows me tht its gonna format whole hdd but syill it has all data

Use the Kubuntu live cd so that you can just boot it to the live OS? If you do run the script and post it in code tags. A live cd will not install unless you tell it to. You can also load the live cd onto a thumb with unetbootin from windows or Ubuntu.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If you have a recovery cd for the windows set up here are the instructions and a http link on how to get to repair besides the instructions I highlighted the one you have to run in the windows terminal.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Here is a link to the recovery cd.
[W7 Recovery](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by wilee-nilee on 2010-06-17
Really I wonder if you didn't wipe the disc with acronis, this would still leave grub in the master boot record and would be showing a grub error on boot. That is why the script is so important here.

---

### Post by ThunddeR on 2010-06-17
tx for the advice 
i will try it and let u kno thanx once again

---

### Post by ThunddeR on 2010-06-18
Thanx dude
it really helped....
I have recovered from the recovery disc successfully

---

### Post by wilee-nilee on 2010-06-18
> **ThunddeR said:**
> Thanx dude
it really helped....
I have recovered from the recovery disc successfully

Thats great I had wondered about the acronis part.

---

