---
title: "[Dual Boot] Removing Ubuntu partion &amp; GRUB safely"
date: 2011-11-30
forum: General Help
---

### Post by ksaul on 2011-11-30
I am currently dual-booting with Windows 7 64bit and Ubuntu 11.04 - well I never use ubuntu anymore ( :( ) and i want to remove it and open up that partition so Windows can use it for more space.. and also I dont want to have to select Windows everytime I boot up so I want Ubuntu & GRUB completely removed..

I tried to do it by myself once before but my boot sequence and MBR got completely ****** and I had to (1) reinstall ubuntu/grub (2) repair windows after i installed ubuntu/grub

so how do I remove ubuntu and grub safely, without doing any damage to my windows partition and boot record/sequence?


(i attached a copy of my partition table if it helps any)

---

### Post by Miljet on 2011-11-30
Perhaps this link might help.  [http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by Mark Phelps on 2011-11-30
First thing you should do is boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You will need that to restore the Win7 MBR.

Then, use the Disk Management utility (still in Win7) to remove the Ubuntu partition.

You can try also using the same utility to grow an NTFS partition to fill the empty space.

Once that is done, reboot using the Win7 Repair CD you just created and run Startup Repair three times -- yes, three times.

And in future, if you have additional Win7-related questions, strongly suggest you visit the windows 7 forum: sevenforums.com.

That should get you booting into Win7 by default again.

---

### Post by ksaul on 2011-12-05
> **Mark Phelps said:**
> First thing you should do is boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You will need that to restore the Win7 MBR.

Then, use the Disk Management utility (still in Win7) to remove the Ubuntu partition.

You can try also using the same utility to grow an NTFS partition to fill the empty space.

Once that is done, reboot using the Win7 Repair CD you just created and run Startup Repair three times -- yes, three times.

And in future, if you have additional Win7-related questions, strongly suggest you visit the windows 7 forum: sevenforums.com.

That should get you booting into Win7 by default again.

going to try this - thank you!

---

### Post by ksaul on 2011-12-05
I tried what you said, but with no luck. I ended up having to reinstall ubuntu into the deleted partition to have windows load.
When I deleted the partition, and then loaded the windows repair disk - it repaired the first time fine, and then I ran the program like 7 more times, but it said something about removing portal media devices (so i unplugged ALL usb devices) and ran the progrm again - and still with the same error (meaing it did not even try to repair the boot record)

When I would restart (After trying to repair the mbr), it kept saying "grub rescue> "

so i installed ubuntu 11.04 again, and now i can launch windows again but i still have the GRUB bootloader, and ubuntu installed :(

---

### Post by Mark Phelps on 2011-12-05
IF it continued to say GRUB rescue, then GRUB still remained on the drive.  Do you have more than one drive?

Try using Boot-Repair: 

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by mystika1 on 2011-12-05
Hi,
When I needed to remove linux from a dual boot system I made a live cd of parted magic. I booted the live cd and deleted the linux partitions and resized the windows part to the entire drive. I then booted the windows 7 cd and instead of choosing "install" I choose repair.(on the lower part of the screen). A menu comes up to choose options...select command prompt and type "Fix MBR" If I remember correctly you will have to verify that you are sure you want to perform this action by entering a y for yes. That should fix your problem and you should boot normally. I hope that I included all of the steps cause it has been a while but if you have trouble let me know. I wrote the steps down in my windows 7 case...I am just to lazy to go digging in my closet at the moment.:D

HTH,

Penny

---

### Post by i D on 2011-12-05
Go to Windows.  Delete the Ubuntu Partition. 
Restart the PC and you will get GRUB error. 
Start Win 7 cd.
Click on the "Repair Your Computer" option to gain access to the System  Recovery window. Now choose "Command Prompt" to run the Bootsect.exe  utility. Bootsect is located inside the boot folder so change your  directory to boot. Now run "bootsect /nt60 C:\" (without quotes) if you  had Windows 7 initially installed in the C partition. Alternatively, you  can run "bootsect /nt60 SYS" or "bootsect /nt60 ALL" (without quotes)  to repair the system partition or all partitions. Eject the DVD  and  restart your computer. Your computer should now boot Windows 7 again.

---

