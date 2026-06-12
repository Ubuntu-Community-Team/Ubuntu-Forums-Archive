---
title: "Help with slave HDD and Gparted..."
date: 2006-03-29
forum: General Help
---

### Post by WackToMack on 2006-03-29
Hello people!  So, I have a slave HDD connected and I want to partition it with Gparted so that I am able to backup/store my music, movies, documents, etc onto it.  I have no idea how to use Gparted, and the Wiki/Documentation didn't really help at all, so I was wondering if somebody could give me a quick walkthrough of sorts to set up my slave HDD to do this.  Thanks in advance! :D

---

### Post by aysiu on 2006-03-29
Well, you click on the partition you want to delete.
Then you right-click it and say you want to delete it.
Then you click the apply button (I think it's a checkmark) to apply the changes.
Once that's happened, right-click and create... create it however you want--FAT32 or Ext3. And apply the changes again.

[Screenshots](http://gparted.sourceforge.net/screenshots.php) may be more useful to you than the Wiki.

Once you've reformatted it, post here what filesystem you're using (FAT32, Ext3), and I or someone else will give you instructions for how to add it to your /etc/fstab

---

### Post by gerbman on 2006-03-29
[QUOTE=WackToMack]Hello people!  So, I have a slave HDD connected and I want to partition it with Gparted so that I am able to backup/store my music, movies, documents, etc onto it.  I have no idea how to use Gparted, and the Wiki/Documentation didn't really help at all, so I was wondering if somebody could give me a quick walkthrough of sorts to set up my slave HDD to do this.  Thanks in advance! :D[/QUOTE]
Hi there. First, make sure the slave drive isn't mounted anywhere. Then fire up GParted and make sure the slave drive is selected in the top-right corner. Again, *make sure* the slave drive is selected. If you want to do a complete wipe of the slave drive, delete any partitions you see displayed. Then create a single partition to fill up all the free space. I would suggest formatting the drive as a FAT32 partition, but people have different opinions on this one. FAT32 will definitely work though. Last, check out [this]("https://wiki.ubuntu.com/AutomaticallyMountPartitions") page for info on mounting the new drive.

Of course, it is always a good idea to back up any critical data before even starting GParted. Chances are you won't have any problems, but you'll be kicking yourself the one time you don't and you lose a partition.

---

### Post by gerbman on 2006-03-29
[QUOTE=aysiu]Well, you click on the partition you want to delete.
Then you right-click it and say you want to delete it.
Then you click the apply button (I think it's a checkmark) to apply the changes.
Once that's happened, right-click and create... create it however you want--FAT32 or Ext3. And apply the changes again.

[Screenshots](http://gparted.sourceforge.net/screenshots.php) may be more useful to you than the Wiki.

Once you've reformatted it, post here what filesystem you're using (FAT32, Ext3), and I or someone else will give you instructions for how to add it to your /etc/fstab[/QUOTE]
I even said to myself "I bet aysiu gets to this one before I submit"...kudos

---

### Post by WackToMack on 2006-03-29
Ah, I see.  This is quite simple to do... lol.  I ended up using a fat32 partition.  Now, how do I edit my fstab?  Thanks in advance! :D

---

### Post by gerbman on 2006-03-29
[QUOTE=WackToMack]Ah, I see.  This is quite simple to do... lol.  I ended up using a fat32 partition.  Now, how do I edit my fstab?  Thanks in advance! :D[/QUOTE]
[This]("https://wiki.ubuntu.com/AutomaticallyMountPartitions") page describes exactly how to do that. See the section "Mounting partitions manually". The line in my fstab that mounts my second hard drive is the following:```
/dev/hdb1       /mnt/hd2        vfat    defaults,uid=gerb       0       0
```Hope that helps.

Edit:  That guide seems a little wordy. Basically, the first column in fstab is the partition to mount, the second is where to mount it (a folder you create), the third is the filesystem type (vfat for FAT32 partitions), the fourth specifies options, and the last two can usually be set to zero (I forget what they do, but I've never had problems with zero).

---

### Post by WackToMack on 2006-03-29
Thanks for the quick replies.  I mostly used the fstab format that gerbman has, only I replaced "uid=gerb" with "uid=wacktomack".  Hey gerbman, do you use your second hard drive to store and backup files also?

---

### Post by gerbman on 2006-03-29
[QUOTE=WackToMack]Thanks for the quick replies.  I mostly used the fstab format that gerbman has, only I replaced "uid=gerb" with "uid=wacktomack".  Hey gerbman, do you use your second hard drive to store and backup files also?[/QUOTE]Yup! I have all my music and movies on the second hard drive. It's also easy to share the drive with Samba if you're interested (so you can access the drive from a second computer or laptop, for example).

---

### Post by WackToMack on 2006-03-29
Cool.  That was the perfect setup then.  Thank you gerbman!  You made my night go a whole lot smoother..lol. :D

---

### Post by gerbman on 2006-03-29
[QUOTE=WackToMack]Cool.  That was the perfect setup then.  Thank you gerbman!  You made my night go a whole lot smoother..lol. :D[/QUOTE]Totally welcome...in case you haven't seen [this]("http://ubuntuforums.org/showthread.php?t=151294") thread, responses like yours probably play a big role in keeping this forum as good as it is. Pass the knowledge along!

---

