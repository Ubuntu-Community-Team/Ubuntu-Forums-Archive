---
title: "How do I delete windows partition and resize Ubuntu partition?"
date: 2011-04-23
forum: General Help
---

### Post by Murdoc419 on 2011-04-23
Hey guys, I am ready to remove my Windows partition but I am not quite sure how. I have installed Gparted. I'm guessing it's probably as simple as selecting the partition and hitting delete. However I have 4 different partitions: sda1 which is labeled recover and is 11GB, sda2 which is labeled system reserve which is 100MB and sda 3 which is 193GB. They are all NTFS file systems so I should be able to get rid of all of them, right? I used the Vaio recovery software on my laptop to create recovery disks so if anything goes wrong I can at least reinstall Windows long enough to download Ubuntu :) Is this how I remove the Windows partition? Then I just need to know how to resize the Ubuntu partition to use the entire hard drive. Sorry for the wall of text just wanted to give enough info. Thanks in advance.

---

### Post by ghostborg on 2011-04-23
Just be carefull with recovery discs they usually just restore the Windows operating system to your C partition by using another partition on your existing hardrive where an image of the operating system is located and then loads all the crapware back on like the day you bought it. I do think that the Sony Vaio recovery discs restore the operating system from the discs you made. Just double check before you blow away any partitions. I think even so they would send or you could download what you need by calling them.

If you are going to use the entire drive as Ubuntu there is an option during the install to "Use entire drive" which should automatically partition and format the drive for you.

If you are using wireless you might want to have a lan cable or direct connection available in case the wireless doesn't work right away.

---

### Post by Murdoc419 on 2011-04-23
I already have Ubuntu installed on one partition so I shouldn't have to reinstall should I? I was thinking I should just be able to resize it. I didn't realize that about the recovery partition. I will probably just keep that partition then since it is only 11GB just in case I need to preform a recovery. But can I just resize the Ubuntu partition somehow or do I need to do a fresh install?

---

### Post by lithopsian on 2011-04-23
Your post is a little confusing.  You mention four partitions, but only describe three NTFS partitions.  I assume the other is some sort of Ubuntu filesystem, probably ext4?  You also say you have installed gparted, which wouldn't normally be necessary.

The answer to the question I think you're asking is that yes, you can delete non-Ubuntu partitions and then resize your Ubuntu partition without reinstalling.  It may be as simple as "unmount, delete, resize" but there are some things that could spoil your day.  Don't do this from Ubuntu, or at least not the resize bit.  Boot from a Live CD because you can't mess with partitions that you're using.  You may have trouble resizing if the unallocated space (after deleting) is not nect to the Ubuntu partition, or if the unallocated space is not on the same extended partition.  It can still be done, just a couple of extra steps.

Got swap?  You don't have to have a swap partition but now would be the time to get one if you need one.

Got Live CD?  Because obviously if you have and if it works then you don't need any Windows recovery disks to get you back on the internet when everything crashes and burns.

P.S.  S picture is worth a thousand words.  Post a picture of the partitions as shown by gparted and we can give much more precise instructions.

---

### Post by Quackers on 2011-04-23
Are your Vaio recovery discs two dvd's? If so they will likely give you the opportunity to recover the whole system (including recovery partition) or to just restore the C: partition. That's what mine do.
Have you checked to see if they work? Don't wait until you need them to find out they don't work. I have 3 sets of 2 dvd's - just in case.

You should be able to delete all the Windows partitions from within gparted. I would then suggest that you run ```
sudo update-grub
``` afterwards to empty the grub menu.
Alternatively you could use the gparted from the live cd desktop.

---

### Post by Murdoc419 on 2011-04-23
Yes sorry I just read over my first post and it was a bit confusing. The fourth partition is the Ubuntu partition. You'll see in the screen that it is split into two parts. I'm not sure what the different parts of the partition are for. However, I thought about it and I don't have too many files on my Ubuntu partition that I need to keep. I can back up what I need onto my flash drive. There also aren't many programs that I would need to re-download. (I just recently installed Ubuntu beside Windows) So in this case would it be better for me to just backup my files and do a clean install of Ubuntu? 
Just in case here is the screen:

[[IMG]http://img826.imageshack.us/img826/2816/parions.png[/IMG]](http://img826.imageshack.us/i/parions.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

