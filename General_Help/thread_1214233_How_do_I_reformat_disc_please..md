---
title: "How do I reformat disc please."
date: 2009-07-15
forum: General Help
---

### Post by scotttie on 2009-07-15
Hello,
I have an HP 510 Which had a corrupt root it would not start or go into recovery, the only option was to load Ubunto 8.10 and use the whole disc to wipe out all window files, this worked OK, I use Ubunto on another PC so I now need to reformat the disk on the hp 510 laptop to reload windows (inserting the Windows recovery disc does not work it just loads Ubunto every time) is there a command to reformat the hard drive so I can put XP back on Please.

thanks very much

Scottie

---

### Post by lisati on 2009-07-15
My first thought about your recovery disk(s) is that maybe you need to tell your computer's BIOS settings to boot from CD. There's usually something displayed when you turn your computer on allong the lines of "Press F1 to do such-and-such" - pressing F12 on my laptop lets me choose where to boot from, and on my desktop it's the Esc key.

Starting an Ubuntu "Live CD" to use it to wipe things clean and do a fresh install of Ubuntu will be similar.

---

### Post by t4thfavor on 2009-07-15
+1 above. It needs to boot from the recovery disk in order to load the recovery software.

---

### Post by egalvan on 2009-07-15
> **t4thfavor said:**
> +1 above. It needs to boot from the recovery disk in order to load the recovery software.

+1 also....

and to get it to boot from the CD, there are two options...

1) change the boot order in the BIOS

2) wipe the hard drive so the  boot sequence skips the empty drive and goes on to the CD drive (a trick I use when the BIOS is locked :p )

So everyone is right... :lolflag:

---

### Post by scotttie on 2009-07-15
HI thanks for reply , I have checked BIOS and boot order is OK cd 1st  but it still wont load windows recovery disc just straight into Ubunto, I thought if I could reformat the drive then try the disc it should work but I don't know the command to refomat in Ubunto speak.

thanks
Scottie

---

### Post by phillw on 2009-07-15
Hi, 

you will have to ensure that your BIOS is set to boot from the CD/DVD drive 1st, before the Hard-Drive.

That will force the computer to kick in the Windows disk.

Now, when it comes to putting XP on a computer - after many attempts, many different ways - I use a windows 98 SE install disk to format the disk, then install 98. It may seem a long way round, but, it has never let me down. XP doesn't seem to come with the tools to re-format a disk !!!

To take a backup of your exisiting Hard drive, please follow the excellent instructions here ...

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore)


The next command will wipe your boot sector and is irreversible - YOU MUST ENSURE THAT YOU HAVE EVERYTHING YOU NEED OFF THE HARD-DRIVE.  YOU DO _**NOT**_ GET ANY SECOND CHANCE.


  If you have ever tried to repartition a LINUX disk back into a DOS/Windows disk, you will  know that DOS/Windows [COLOR=#0040a0]FDISK[/COLOR] has bugs in it that prevent it from recreating the  partition table. A quick: 



    [COLOR=red]   
 [/COLOR][COLOR=blue]  dd if=/dev/zero of=/dev/hda bs=1024 count=10240

 [/COLOR]
  will write zeros to the first ten megabytes of your first IDE  drive. This will wipe out the partition table as well as any  file-system and give you a ``brand new'' disk.    
  

PLEASE BE CAREFUL - IT IS THE KISS OF DEATH TO YOUR DATA.

Regards,


Phill.

---

### Post by zot171 on 2009-07-16
i believe one of your problems is that you are trying to use a **windows _recovery_ disc** instead of a **windows _installation_ disc** the recovery disc contains drivers and tools to help you recover a malfunctioning system thats already installed, not install a new one...

---

### Post by Superd00per on 2009-07-16
> **zot171 said:**
> i believe one of your problems is that you are trying to use a **windows _recovery_ disc** instead of a **windows _installation_ disc** the recovery disc contains drivers and tools to help you recover a malfunctioning system thats already installed, not install a new one...
As a matter of fact, with laptops etc, you get Windows Recovery Discs, it's basically GHOST on a cd with an image of a pre-installed OS, it basically gets your OS back into the state it originally was when you bought your laptop or pc.

---

