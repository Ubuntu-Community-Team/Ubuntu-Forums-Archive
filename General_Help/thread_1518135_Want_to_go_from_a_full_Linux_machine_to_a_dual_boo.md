---
title: "Want to go from a full Linux machine to a dual boot machine with Windows 7"
date: 2010-06-26
forum: General Help
---

### Post by VinoFuriaRoja on 2010-06-26
Hey there,

I first installed Lucid 10.04 a few months ago, and completely deleted Windows XP from my machine.  I made it a full Linux machine on my hard drive, etc..  What I want to do now is put Windows 7 on the computer so that my wife can use it to her hearts content, without having to fuss over just virtualizing it in Virtualbox.  She is not computer savvy!  

So, how can I go about doing this, without disrupting my Linux that I have now?  Can I partition the drive and then install Windows on that partition?  I do not need a lot of disk space partitioned....just enough to start up Windows, surf the net, and for her to use iTunes.  

Any help would be GREATLY appreciated...including step by step instructions. 

Thanks. 

Mark

---

### Post by Zerocool Djx on 2010-06-26
Yea just make sure you direct the windows installer to use that partition you created.. then when win is installed install grub... that should do it..

---

### Post by wilee-nilee on 2010-06-26
> **VinoFuriaRoja said:**
> Hey there,

I first installed Lucid 10.04 a few months ago, and completely deleted Windows XP from my machine.  I made it a full Linux machine on my hard drive, etc..  What I want to do now is put Windows 7 on the computer so that my wife can use it to her hearts content, without having to fuss over just virtualizing it in Virtualbox.  She is not computer savvy!  

So, how can I go about doing this, without disrupting my Linux that I have now?  Can I partition the drive and then install Windows on that partition?  I do not need a lot of disk space partitioned....just enough to start up Windows, surf the net, and for her to use iTunes.  

Any help would be GREATLY appreciated...including step by step instructions. 

Thanks. 

Mark

Post a screen shot of gparted. Also run this command in the terminal and post the answer from the terminal.
```
sudo grub-install -v
```

---

### Post by VinoFuriaRoja on 2010-06-26
```
mark@mark-laptop:~$ sudo grub-install -v
[sudo] password for mark: 
grub-install (GNU GRUB 1.98-1ubuntu6)
mark@mark-laptop:~$ 
```

this is what i get for grub and the image is from Gparted.  What next?  What is the best way for me to partition my disk and then install Windows XP on it without losing my current Linux setup?

---

### Post by wilee-nilee on 2010-06-26
> **VinoFuriaRoja said:**
> ```
mark@mark-laptop:~$ sudo grub-install -v
[sudo] password for mark: 
grub-install (GNU GRUB 1.98-1ubuntu6)
mark@mark-laptop:~$ 
```

this is what i get for grub and the image is from Gparted.  What next?  What is the best way for me to partition my disk and then install Windows XP on it without losing my current Linux setup?

So really I would just using the live Ubuntu Cd open gparted turn off swap with a right click and shrink the main ext4 partition to the right leaving enough room for W7. W7 unpacks to at least 10 gigs with the pro version so I would split the HD in half to be safe. Build a ntfs partition with gparted, then use the custom install option with W7 to install to that premade partition. Then If all goes well use this link to reinstall grub to the mbr sda.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I have had the Ubuntu go unallocated when I don't prebuild that ntfs partition and install W7 straight into it.

Also any time you change a partition you want to have stuff backed up in case something goes wrong. Really having a external HD in this situation for media would make things safer. Some people have a separate home partition and just leave that stagnate and if they change a distro just install in a separate partition. Chances are you will lose nothing here when you resize the ext4, but as the famous rooster foghorn leghorn says, always keep your feathers numbered for such a occasion.

The only other thing I'm noticing is that the swap is in a extended partition so this is no big deal. If you build a partition setup for a Ubuntu install before installing make the extended first, then put a primary=ext4 here inside leaving enough space for the swap partition. A HD can only have 4 primaries, but if you use a extended you can actually have many more primaries inside of it so if you had a much bigger HD you could have a multiple amount of Linux distros in that extended with just one swap.

---

### Post by oldfred on 2010-06-26
You want to make sure you install windows to a primary partition sda1- sda4. 

If you use one primary as an extended as you have then you can have logicals inside the extended. Then you only can have three primaries. Windows needs a primary to install into.

---

### Post by pitisjol on 2010-06-26
hi buddy as wilee-nilee suggest i would use the live cd to get the partitions into place. 
remember to leave the space for windows at the beginning of the hd and linux at the end with the swap off.
also remember that windows 7 (i am not sure about xp) also uses a 100mb partition for the windows boot  (it is created automatically) which is also primary. that is to say that at the end of the installation you will have 2 partition for windows and 1 for linux. if you have to create a swap that is fine but if you would also like to create a fat partition to be shared between the 2 systems both the swap and the fat will have to be "extended" partitions rather than logical.
then to recover the grub i found that the instructions in this page are pretty easy and work well (linux lucid uses the grub2 instead of the grub)
[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB#Usando_una_distribuci.C3.B3n_Live](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB#Usando_una_distribuci.C3.B3n_Live)
(i have recently done the installation as you want yours and runs perfectly).
good luck

---

### Post by Mark Phelps on 2010-06-27
Win7 only creates the small boot partition on an unformatted drive.

If you create an NTFS partition at the beginning of the disk, when you install Win7, have it reformat that partition; then, continue with the install normally.  I have found from experience that it's better to let Vista and Win7 do their own formatting.

---

