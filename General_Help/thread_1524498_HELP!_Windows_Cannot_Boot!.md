---
title: "HELP! Windows Cannot Boot!"
date: 2010-07-05
forum: General Help
---

### Post by fDurdenC on 2010-07-05
I was running a dual boot lap top with ubuntu and windows 7. I decided to delete ubuntu and did so in windows. Once I restart my computer i get a black command screen that says unknown file system grub rescue. Nothing I do works. I made a windows 7 repair disc on a friends computer and it doesn't work...Ive typed numerous things in the command that I've seen on forums and they don't work either. I need major help!

---

### Post by WorMzy on 2010-07-05
Deleting Ubuntu removed the files that grub needed to work. You need to reinstall the Windows bootloader to the mbr using the recovery CD or the original Windows installation CD.
[http://www.google.co.uk/search?q=reinstall%20windows%20bootloader%20to%20mbr](http://www.google.co.uk/search?q=reinstall%20windows%20bootloader%20to%20mbr)

---

### Post by gopi_tux on 2010-07-05
get a lived cd

fix grub

go to command line
type 
sudo -i
grub
root (hd0,n) //n being the partiton of ubuntu -5th partiton means 4
setup (hd0)


reboot

---

### Post by WorMzy on 2010-07-05
S/he deleted the Ubuntu partition, so fixing grub isn't an option.

---

### Post by fDurdenC on 2010-07-05
Every command i type in the line comes back unknown command " "

---

### Post by philinux on 2010-07-05
See section #16 to restore windows MBR from the livecd without the need for a windows cd.
Or use your windows cd.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by wilee-nilee on 2010-07-05
If you still have everything in order in W7 this is the recovery disc link.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

And here is a list of commands with a http address and instructions on how to get to the command line on a recovery in Windows vista and w7. Just get to the command line using the recovery disk and run the highlighted command.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[I][U]
Post #6 the one above me will work fine as well.[/U][/I]

---

### Post by fDurdenC on 2010-07-12
Things still arent looking good. I'm not too computer savvy but when i put in the windows repair disc nothing comes up i still get a black screen that says "error unknown file system." with "grub rescue>" under it awaiting a command.

I insert the disc restart with CTR alt del and nothing happens.

I dont want to have to take this to geek squad and have them charge me more than the computer.

---

### Post by michealdbrown on 2010-07-12
press delete over and over when you start your system(or f2/f8 depending on make/model) go into your bios and go to boot order, and change the boot order so that the drive that your recovery CD/DVD is in is BEFORE your harddrive.  reboot, and when you do, you should get a message that says "press any key to boot from CD/DVD"  press any key and follow the directions that were given above to repair the isntallation/reinstall the MBR from tyour windows installation disk.

---

### Post by fDurdenC on 2010-07-12
Thank you i will try this

---

### Post by fDurdenC on 2010-07-12
f2 worked and the windows CD loaded beautifully! Thank you! Now in the command prompt I am to input the 5 commands from post 7?

---

### Post by screaminfakah on 2010-07-12
Hey, you can follow the other posts on how to fix it but I have always just used the program SuperGrub disc.  
The only thing is that you have to have access to a computer that isn't borked and know how to make a .iso disc after you download supergrub.  Supergrub does everything else.

Good luck

---

### Post by fDurdenC on 2010-07-12
**BootRec.exe /fixmbr **fixed everything i now have windows back and running. You guys/girls are the best! Thank you all! just one more question should I do a BootRec.exe /fixboot too or is everything fine as is?

---

