---
title: "Problem with Grub"
date: 2006-04-11
forum: General Help
---

### Post by jsvidyad on 2006-04-11
Hi!!!


  I am having some problems with GRUB. I had some 5GB of empty space on my hard drive. I have a dual boot system with windows and ubuntu. I wanted to convert the empty space to FAT32 in order to share files between linux and windows. I first created the file system on ubuntu but windows did not automatically mount it. So, I recreated the FAT32 file system using windows. Then, i rebooted. Now, GRUB starts to load and then gives an error message saying "Error 15". I am not sure what this means. Before this happened, the / partition was on /dev/hda9 and /home on /dev/hda6. After this happened, I noticed upon checking with GParted on the livecd that now / is on /dev/hda6 and /home is on /dev/hda9. I am not sure how this switch happened. 

Any Help would be really appreciated.

I am using the live CD right now.](*,)

---

### Post by dmj99 on 2006-04-11
I'm not at my Linux computer right now, so its difficult to give a complete answer.  It sounds like you added a new partition on your disk before your Linux partition.  If so, you have to tell grub what partition to look in to find Linux (because its partition number has changed).  It is possible you will need to edit your menu.lst file which is in your boot/grub folder to reflect changes in your disk partitions.  If you don't have a boot floppy, you can edit commands in grub to boot up.

---

### Post by jsvidyad on 2006-04-11
Whew. Managed to solve that problem. Just followed the instructions in  a previous thread.

---

### Post by Mustard on 2006-04-11
[QUOTE=jsvidyad]Whew. Managed to solve that problem. Just followed the instructions in  a previous thread.[/QUOTE]

It might be worthwile to show that link in this thread, for the next person who comes along. :)

---

### Post by Soarer on 2006-04-13
Me for example :) 

See: [http://ubuntuforums.org/showthread.php?p=917436#post917436](http://ubuntuforums.org/showthread.php?p=917436#post917436)

---

### Post by jsvidyad on 2006-04-13
The link I followed was [http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

---

### Post by Mustard on 2006-04-16
[QUOTE=jsvidyad]The link I followed was [http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)[/QUOTE]

Well done. :)

---

