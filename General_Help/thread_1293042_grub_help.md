---
title: "grub help"
date: 2009-10-16
forum: General Help
---

### Post by 314 on 2009-10-16
ok i hope i didn't mess up lol. ok so heres my issue that i need a tissue.

first my system specs

intel core I5 
4gb dd3 ram
ubuntu 9.04 64bit
1tb wd green sata2 hdd
200gb maxtor sata hdd
500gb wd sata hdd
nvida 9600gt
dvd burner

ok so i like ubuntu so i figured i'd install.
it installs fine then like an idiot i removed the 200gb
then i get a grub error 21. so i say fine i plug it back in. now i get a grub error 17. heres my real delema i am pretty sure that the grub installed itself onto the 1Tb but the partitions are all on the 500GB. I cant have the MBR of the 1TB touched. so i am asking Please help me fix it.

---

### Post by schnauzer93 on 2009-10-16
Try reinstalling grub:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by 314 on 2009-10-16
but that still doesnt help me restore my 1tb mbr

---

### Post by ackley on 2009-10-16
Do you have other operating systems on this computer? 

What's the ideal setup you're going for here?

I guess I'm not really following what you're wanting out of this. You say in your first post that you don't want the mbr touched, but in your second post you want to restore the mbr on your tb drive.

o.O

---

### Post by 314 on 2009-10-16
ok heres whats going on the 1tb has ntfs but no os on that drive the 200gb has xp installed and the 500gb has ubuntu

i am not sure what hdd has the mbr portion of grub on it but i want all linux things grub and everything on the 500GB so that only the 500 is touched

---

### Post by 314 on 2009-10-16
i just want all traces of the 1tb to be free of grub and linux

---

### Post by ackley on 2009-10-16
Ok, so you want grub to be installed on the 500 gig drive where linux is. And the 200 gig has XP on it. And, I'm assuming, use the terabyte drive just as storage for whatever you'd like. Here's how I would go about setting that up. 

First of all, find out your drive names by typing this command in a terminal.

```
sudo fdisk -l
```If all your drives are plugged in, you'll see them listed in a fasion such as this:

```
tristan@eee:~$ sudo fdisk -l

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         490     3935893+  83  Linux

Disk /dev/sdb: 2013 MB, 2013265920 bytes
64 heads, 63 sectors/track, 975 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00079c3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         976     1965952+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(974, 63, 63) logical=(975, 15, 15)
```That's my output of fdisk -l on my eee pc with a two gig sd card formated as fat32.

Ok, let's say that your 200 gig drive is labeled as "sda", your 500 gig is "sdb" & your terabyte is "sdc". Here's how you would install grub to your 500 gig drive or "sdb".

Open a terminal and type:
```
grub
root (hd1,0)
setup (hd1)
quit
```Let me explain a little about grub. Grub counts from 0 to 9. Where as linux counts from 1-9. So "sda" would be "hd0", "sdb" is "hd1" etc..

Grub also does this for partitions, too. If you have multiple partitions for your linux setup, such as "sdb1", "sdb2" & "sdb3", grub will see this as "hd1,0", "hd1,1" & "hd1,2" respectively. As you can see in this example, I used your 500 gig. 

Hopefully all of that makes sense. Also, these names are just examples that I used. Your layout may vary from this. 

If you have anymore questions or if someone can explain this a little clearer than I did, by all means, post away. :D

OH! Another thing I forgot to mention, you want to install grub to your /boot partition if you have one. If not, it's just in your / partition.

---

### Post by 314 on 2009-10-16
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa376388e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb63ee5ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe2fbe2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       59350   476728843+  83  Linux
/dev/sdc2           59351       60801    11655157+   5  Extended
/dev/sdc5           59351       60801    11655126   82  Linux swap / Solaris


also i know that grub is installed on hd2,0 so that would be my 500 correct.

so if i read you right i would want to do this

grub
root (hd2,0)
setup (hd2)
quit

---

### Post by ackley on 2009-10-16
Looks right to me. Another thing I forgot about, you may have to tell the BIOS to boot from a slave disk if the 500 gig drive isn't set as the master. Otherwise, you may have to install grub on the master drive. Which, honestly, I have no clue how to do as I haven't dual booted with windows since before Vista.

---

### Post by PrePenguin on 2009-10-16
> **314 said:**
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa376388e
 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 121601 976760001 7 HPFS/NTFS
 
Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb63ee5ae
 
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 24791 199133676 7 HPFS/NTFS
 
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe2fbe2f
 
Device Boot Start End Blocks Id System
/dev/sdc1 1 59350 476728843+ 83 Linux
/dev/sdc2 59351 60801 11655157+ 5 Extended
/dev/sdc5 59351 60801 11655126 82 Linux swap / Solaris
 
 
also i know that grub is installed on hd2,0 so that would be my 500 correct.  
so if i read you right i would want to do this
 
grub
root (hd2,0)
setup (hd2)
quit
 
 
Yea it looks like you are booting from the wrong HD you need to set the bios to boot from the correct drive. The * is the drive its booting from and it is telling you theres no OS on that drive since its just a storage drive so you need to do that.

---

### Post by 314 on 2009-10-16
ok so i set it in my bios that my 500 is primary master and then i try to do the grub but i get error 21: selected disk does not exist

---

### Post by PrePenguin on 2009-10-16
> **314 said:**
> ok so i set it in my bios that my 500 is primary master and then i try to do the grub but i get error 21: selected disk does not exist
 
Ok now try booting from the other HD and see if the MBR is there.. Least we can eliminate this part.

---

### Post by 314 on 2009-10-16
what do you mean to see if the mbr is there. you can't have a usable hard disk without an mbr. but what i have done in gparted is remove the boot flag from the 1tb and added a boot flag to my 500gb

---

### Post by PrePenguin on 2009-10-16
> **314 said:**
> what do you mean to see if the mbr is there. you can't have a usable hard disk without an mbr. but what i have done in gparted is remove the boot flag from the 1tb and added a boot flag to my 500gb
 
 
Meaning as I understand what you said in a previous post you are not sure which drive you installed the MBR on the simplest way if you keep having problems I suppose would be to just re-install Grub. Also we arent concerned in the bios about the primary drive setting as much as what order they boot in.. I am not sure if we have the same thing accomplished here.

---

### Post by 314 on 2009-10-16
i set it so that the first boot is the 500. but how do i reinstall grub lets just do that

---

### Post by PrePenguin on 2009-10-16
> **314 said:**
> i set it so that the first boot is the 500. but how do i reinstall grub lets just do that
 
 
 
**Here’s the quick and easy way to re-enable Grub.**
1) Boot off the LiveCD
2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub “prompt”, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.
[INDENT]sudo grub
> root (hd0,0)
> setup (hd0)
> exit
[/INDENT]Reboot (removing the livecd), and your boot menu should be back.

---

### Post by 314 on 2009-10-16
error 17 cannont mount selected partition

---

### Post by 314 on 2009-10-16
you know what i have had enough i am just gonna reinstall and be done with it

---

### Post by PrePenguin on 2009-10-16
> **314 said:**
> error 17 cannont mount selected partition
   
Did you enter the correct drive i didnt edit that list you would have to yourself with the proper settings for your HD

---

### Post by PrePenguin on 2009-10-16
> **314 said:**
> you know what i have had enough i am just gonna reinstall and be done with it
    
 
Well good luck I am sorry we couldnt resolve this an easier way for you.

---

### Post by 314 on 2009-10-17
no worries it was the easier faster fix for me thanks you anyway

---

