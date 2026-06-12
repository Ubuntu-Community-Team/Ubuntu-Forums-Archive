---
title: "Stupid me... (GRUB)"
date: 2011-04-22
forum: General Help
---

### Post by graboy on 2011-04-22
Hey guys, so I have been running ubuntu along side vista using vista as my primary OS. I have been planning to sell my laptop In order to have enough money to buy a desktop, and I knew I had a useless and empty partitions that I needed to clean up before I sell it. I used a partition manager to delete the main partition that I wanted to delete, but I also found a few other partitions that I was unaware that I had. I decided to delete these too. After that was done i entered the point where the GRUB would normally let me choose what OS to boot into, but instead I got this error:

Error: no such partition
Grub rescue>

You should be able to figure out what's going on.

My problem is that I have no GRUB command line experience at all, and I need you guys to either guide me through booting into vista again (I know I did not delete that partition) or teach me how to format my drive from GRUB so I can reinstall vista. 

Thanks, Graboy

---

### Post by coffeecat on 2011-04-22
What you've done is to delete the partition that had much of the grub code and the grub configuration files on it - most probably your Ubuntu root partition. Grub in the mbr (and embedding area - a part of the HD that comes between the partition table and the first sector of the first partition) cannot now find the rest of itself, hence the error message.

If you want Vista only on that machine, the simplest fix is to re-install Windows booting code to the mbr. If you have a Vista installation DVD or repair CD you can run 'bootrec /FixMbr' from a command prompt. If you don't, you can write equivalent code to the mbr using an Ubuntu live CD. See here for three alternative methods:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

The first - the lilo method - works well.

This will only succeed if the Vista partition has the boot flag set - which it probably has. If you have any problems with any of this, boot up the Ubuntu live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions there and post the contents of RESULTS.txt in code tags as described there.

---

### Post by graboy on 2011-04-22
hey guys, I really don't want to go over everything that happened but thanks to my stupidity I accedentally deleted my ubuntu installation on my dual boot system and now I need to boot into vista through grub. 

Heres the command line im at:

error: no such partition
grub rescue>

So yeah, any help would be highly appreciated.

-Graboy

---

### Post by Quackers on 2011-04-22
You need to either re-install Ubuntu or replace grub in the mbr of the drive with the Windows bootloader. You would do this by booting from the Windows repair/installation disc and running ```
bootrec.exe /fixmbr
``` from the command prompt.

---

### Post by howefield on 2011-04-22
Threads merged.

---

### Post by flutillie on 2011-04-22
I just did the same idiotic thing.

Is there any way to reinstall grub? Or at least access and recover the files from the ubuntu partition, then reinstall ubuntu?

---

