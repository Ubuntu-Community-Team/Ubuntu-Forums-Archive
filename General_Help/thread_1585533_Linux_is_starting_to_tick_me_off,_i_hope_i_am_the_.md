---
title: "Linux is starting to tick me off, i hope i am the cause."
date: 2010-09-30
forum: General Help
---

### Post by Al_is_venting on 2010-09-30
Here is the story/problem.

Day 1. XP was installed  only 1 HD is present.

Day2 HD2 is installed and Ubuntu is installed on it.
       both systems working fine at this time with dual boot

Day 3 HD2 is removed and discarded.

Now WIN does not load " grub rescue> comes up"

My conclusion= Linux moved all boot files to HD2 and wrote boot grub on HD1 WHYYYYY!?!?!?!?  Whole point of having 2 hds was to have two systems completely intendant!!!


How can i  quit out of grub and load XP? I have attempted to repair Boot files for windows and it worked, but i still get grub ********

All i want is to quit out of grub and load back in to windows boot , but i cant figure out how. Nothing useful is coming up in google




Please help me!!

! I hope i am the cause of this bc if its entirely Ubuntus fault then i will resent it for it forever

---

### Post by drs305 on 2010-09-30
Grub is still most likely installed in the MBR of your Windows drive. Even though you removed the second drive with the Ubuntu installation, the MBR of drive 1 still tries to point to the Grub files (which are no longer there).

Reinstalling the Windows bootloader to the drive 1 MBR should restore Windows. You can use Windows to do this or if you are in Linux you can download and use *lilo*:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
It may complain about *lilo* not being fully installed but we our goal is not to fully install *lilo* as a bootloader, so that's ok.

If you still have problems, please run the boot info script and post the results:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by slooksterpsv on 2010-09-30
This has happened to me a few times, the only way I've been able to avoid grub being installed on the first HDD (the one with Windows, when I used windows) was to disconnect one of the cables from the HDD for the computer, then install.

---

### Post by Al_is_venting on 2010-09-30
> **drs305 said:**
> Grub is still most likely installed in the MBR of your Windows drive. 
Beat me to my edit. :)

Do i need to do those commands in LInux system. 

i am in the black after bios Grub rescue> screen now and sudo commands are not working. 

Is there anu way to switch boot systems? I have done the windows boot repair so if i understand it correctly i just need to swithc boot loaders

---

### Post by Al_is_venting on 2010-09-30
Was able to boot after doing "FIXMBR"  . Thank you for all the help, ill be sure to disconnect the HD next time install Ubuntu...after all it is the best :guitar:

---

### Post by drs305 on 2010-09-30
> **Al_is_venting said:**
> Beat me to my edit. :)

Do i need to do those commands in LInux system. 

i am in the black after bios Grub rescue> screen now and sudo commands are not working. 

Is there anu way to switch boot systems? I have done the windows boot repair so if i understand it correctly i just need to swithc boot loaders

You would run those commands from a terminal after booting the LiveCD. You can't run them from the grub prompt.

I was thinking you only have one drive connected at the moment. If you have more than one, make sure that BIOS is pointing to your Windows drive. If you have already restored it and the boot flag is on the correct partition, that may be all you have to do.

If you need it, here is another link for restoring the Windows bootloader:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by lunix- on 2010-09-30
Im no grub expert,   but I have done exactly the same thing as you described several times without any problems.   Grub will install itself on your boot partition or boot folder and it will place it self on the mbr / first 512k or so on the disk. As far as I know it will not touch any other disks unless you tell it to..

In your BIOS you could select the grub disk as your first boot choice. Then it will boot into ubuntu disk as first choice, and still be able to choose the Windows Bootloader (chain booting its called I think)
If you want to use windowsdisk only, by setting windows disk as primary boot choice, it will boot into windows from windows' loader without even knowing anything about linux and grub.. 

What caused your probelem, im not sure but if mbr is damaged try this :
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

You shouldn't give up on linux. That I would consider a huge loss.. though grub can surely give one a headache when not working as desired.  Personally Ive got some kind of love hate relationship with grub..   Now I love it 85% and hate it 15% :D

---

### Post by oldfred on 2010-09-30
If you have an old IDE/PATA system you have to boot thru sda or primary master. With newer SATA drives and newer BIOS you can choose which drive to boot with the BIOS. Then you can install different boot loaders in the MBR of each drive and boot either. Some change boots with BIOS but since grub boots windows also very well, you can just use grub to boot. 

But you have to install grub to the Ubuntu drive. They hide that info behind an advanced button on the last partition screen. From the advanced button you can choose which drive to install grub to.

Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Mark Phelps on 2010-09-30
Unless this has changed recently, GRUB is installed by default to the "first" drive it finds in the PC.  So, even though you installed Ubuntu to the second drive, it still installed GRUB to the first drive.

In future, when installing Ubuntu in a multi-drive system, disconnect the other drive(s).  That will ensure that GRUB is installed to the Ubuntu drive.  You will have to boot from THAT drive after you reconnect the other drives.

---

