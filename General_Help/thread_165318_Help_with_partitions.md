---
title: "Help with partitions"
date: 2006-04-24
forum: General Help
---

### Post by bixin on 2006-04-24
I'm using Gparted, I have 3 unallocated spaces on hard drive how do I combine into 1 "whole" unallocated space, so that I can finish my partitions to dual boot. Don't want to format and start over again but I will.


Thanks

---

### Post by gondilon on 2006-04-24
if your free space are continous, then you should be able to use all the for a partition. If you have a partition dividing them up, you will have to delete and re-create the partitionright next to your other partitions in order to create a continous free space.

---

### Post by bixin on 2006-04-24
this is going to sound stupid, but i better ask as I don't know myself. If I delete them(the partition that is separating them) will everything on that partition  go too? I think it is the drive that i will store my files in, in windows. Its a new install so its nothing there but it says 12 mb are used i didn't put anything there so I am assuming its was files written to it when I formatted it from windows. was that too much information?

---

### Post by red_shrike on 2006-04-24
If you deleta a partition everything on it is going to be permanently lost. I hardly believe you will succeed in moving them without problems, so - make a backup, reformat the whole disk (delete EVERYTHING) and than install Windows first and Linux second. Not vice versa.

---

### Post by bixin on 2006-04-24
Out of curiosity, why should I install Linux then XP?

 I think I got them set up, I resized and I am now utilizing all space on hard drive, the drives are out of order of the how to I used ( in case you are wondering I used this how to [http://www.ubuntuforums.org/showthread.php?t=127884&highlight=dual+boot](http://www.ubuntuforums.org/showthread.php?t=127884&highlight=dual+boot) ) but the order should not present a problem,IMHO, if it does, oh well back to the beginning I go its a new harddrive anyway, so nothing to lose.

:KS

---

### Post by OffHand on 2006-04-24
[QUOTE=red_shrike]If you deleta a partition everything on it is going to be permanently lost. I hardly believe you will succeed in moving them without problems, so - make a backup, reformat the whole disk (delete EVERYTHING) and than install Linux first and Windows  second. Not vice versa.[/QUOTE]
Actually it is easier to install Windows before Ubuntu. It is easier because Ubuntu will automaticly detect Windows but not the other way around.

---

### Post by red_shrike on 2006-04-25
I stand corrected. I was probably too tired to notice the obvious mistake. Yes Windows first and than Linux as subsonic has said. Sorry. I will corrrect original post ASAP.

---

### Post by bixin on 2006-04-25
So like i said, I resized the heck out of them and got the drives that linux needed and I am now, using the power of two OS's(not really but it sounds cool) Everything seems to be working fine just need to do my personal tweeks to Ubuntu and I am done. I am using the Ubuntu side for guests and children that way they don't download something and blow the whole thing up. Thanks for the comments and help everyone. Oh but I have one question, the order of my partitions is linux swap, hda1(the small bit that is used for storage of files and such, made it fat32, now will both OS be able to read things put there?) my /home partition then my root partition, does it matter if they are not together? will it take longer to process because of the seperation? Sorry if it sounds stupid just would like to know. :KS

---

### Post by gondilon on 2006-04-25
if you delete a partition, the data is deleted.

---

