---
title: "Help with gparted and expanding new drive"
date: 2009-07-29
forum: General Help
---

### Post by luke0927 on 2009-07-29
OK i have followed the thread from the ubuntu kung fu book.  I cloned my current ubuntu from a 20GB HD to a 160GB HD using the live CD and ddrescue.  Everything went fine and all is OK.  I know need to expand my partitions but I'm a little confused

Using Gparted on the live CD

on my setup /dev/sda1 is the ext3 and is the primary partition with 14.92 GB's used so thats where all my data currently is and the partition I need to grow.

/dev/sda2 is extended and its 839MB
/dev/sda5 is linux Swap.

How do i grow the ext3 partition. All i can seem to grow is the ext or linux swap.  If I right click those i can drag it out and add more space on the Ext 3 I cannot.  I think i just don't have a very good grasp on linux filesystems. 

Thanks for any help!

---

### Post by starcraft.man on 2009-07-29
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

Gparted has great documentation, read em top to bottom in your preferred language. Comes with pics too. You'll probably want to pay extra attention to resizing and getting free space sections.

---

### Post by michy99 on 2009-07-29
Can you post a screenshot from gparted? Understand that you can only expand a partition if there is empty unallocated space next to it. Otherwise, you have to move something first.

---

### Post by luke0927 on 2009-07-29
I'm on my laptop the box running live CD is on the network how can i post a screen shot would i need to paste it in a doc first?

Thinking in windows terms what it looks like is my current disk is there /dev/sda1 and the new space (unallocated) is there its 130GB. I can format that and it will be usable but it will be another partition like a drive F: I wanted to merge the new space with my current /dev/sda1 

I can grow the extended partition to that space as well as the linux swap but not the ext3.  I wonder if i set it up wrong when i installed ubuntu.  



Let me see if i can add some screen shots

---

### Post by Buuntu on 2009-07-29
I believe the unallocated space has to be to the right of it in gparted.  I had the same problem and I fixed it by copying my new partition to the unallocated space and then deleting my old partition.  Kind of a pain, but it works.

---

### Post by drs305 on 2009-07-29
I wrote a guide on expanding the / system partition recently because a lot of new users were ending up with 2.5GB system partitions. Although that is not your situation, the process would be about the same. Here is the link:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by michy99 on 2009-07-29
To post a screenshot, click "Manage Attachments" in the Additional Options section under the Reply area.

Here is a good overview of expanding partitions:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by luke0927 on 2009-07-29
Here are the screen shots

after clone 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122862&stc=1&d=1248898166[/IMG]

Right clicking on the ext3 saying resize/move notice i cannot expand any more to the right

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122863&stc=1&d=1248898166[/IMG]


showing i can expand the extended FS

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122864&stc=1&d=1248898166[/IMG]

after increasing the extended partition I can expand the swap but still not the EXT3

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122865&stc=1&d=1248898166[/IMG]

---

### Post by drs305 on 2009-07-29
Take some time to read the link I provided. You can't expand across the light blue border of the extended partition (in simplest terms).

The easiest thing for you to do is delete the swap partition, delete the extended partition, grow your linux partition, then recreate the extended partition and the swap partition in the space you don't use for your system partition. Moving partitions is going to take a lot longer than just deleting those empty ones (assuming the unallocated space is really empty).

---

### Post by luke0927 on 2009-07-29
I read the problem is you cannot expand a partition unless the unallocated is touching the partition.  So since my extended and swap are between the EXT3 and the unallocated that's why.  I guess I'll have to see if I can move the swap/extended further out in the unallocated and then expand the ext3.  

if not I guess i will have to just expand the extended and use that for new storage.  I would think i would have to auto mount that partition and just place my files in there.

I will go through the link you posted maybe it will tell me if i can move the partitions around...If anyone has any idea's please chime in.

Thanks

---

### Post by drs305 on 2009-07-29
We posted at about the same time. Read post 9 and if you have any questions please ask.

---

### Post by luke0927 on 2009-07-29
> **drs305 said:**
> We posted at about the same time. Read post 9 and if you have any questions please ask.


Thanks just saw that post! and thats exactly what i was going to ask if i should do.  I really appreciate your help!

---

### Post by michy99 on 2009-07-29
The easiest thing is definitely to delete the swap and extended partitions and then make a new swap after you grow the system partition. Be aware that you may have to edit your fstab file to point to the new swap partition, but don't worry about that until you get the partitions the way you want them.

---

### Post by luke0927 on 2009-07-29
> **michy99 said:**
> The easiest thing is definitely to delete the swap and extended partitions and then make a new swap after you grow the system partition. Be aware that you may have to edit your fstab file to point to the new swap partition, but don't worry about that until you get the partitions the way you want them.


will it boot correctly or would i need to look at fstab from the live CD?  I'm making the changes now.  I just removed the extended and swap and made a 2GB swap.

---

### Post by michy99 on 2009-07-29
It will boot fine, you just might not have a working swap partition. It is easy enough to fix. I'm not sure if it will need to be or not. We can look at it when you get done with the partitioning.

---

### Post by Buuntu on 2009-07-29
This is what I suggest:
1.)First copy your old partition the the unallocated space. (right click on the old partition)
2.)Then delete your swap partition.  You will have to swap off.
3.)Extend the new partition to use all of the unallocated space (or as much as you need).
4.)Delete the old partition.
5.)Create a swap out of the unallocated space freed by deleting your swap and the old partition (the unallocated space should have merged).

This is probably what I would do.  If you want to play it on the safe side, you might want to keep the old partition until you are sure the new partition runs error free.

---

### Post by luke0927 on 2009-07-29
Ok I booted with the new drive and everything seems OK.  I changed /etc/fstab to show the new swap as /dev/sda2, and turned on swap.

Is there any where else i need to change swap to show the new partition as /dev/sda2

luke@luke-desktop:~$ sudo blkid -c /dev/null
[sudo] password for luke: 
/dev/sda1: UUID="70112e6f-9a6b-4d4e-ae8a-3e15b0c9a24c" TYPE="ext3" 
/dev/sda2: UUID="6fd83b0b-f13d-41f4-83da-ea550211b7a0" TYPE="swap" 

Thanks again!

Luke

---

### Post by drs305 on 2009-07-29
You want to make sure the correct swap is registered in initramfs. You can compare your current swap UUID and the one stored in Resume with the following command:
```

sudo blkid -c /dev/null | grep "swap" 
cat /etc/initramfs-tools/conf.d/resume

```

If they aren't the same:
```

sudo swapoff -a
gksudo gedit /etc/initramfs-tools/conf.d/resume

```
Replace the existing UUID with the new one from the blkid command, save the file, run the following commands and you are done.
```

sudo update-initramfs -uk all
sudo swapon -a
free -m

```

The "free-m" command should show your swap usage. The middle value can be 0 (not in use) but you don't want ALL zeros.

---

