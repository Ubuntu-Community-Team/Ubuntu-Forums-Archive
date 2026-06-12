---
title: "more hard drive space"
date: 2006-04-06
forum: General Help
---

### Post by ncappel1 on 2006-04-06
I have a second hard drive that is set up as the slave in my computer. It is recognized as a drive in my computer, as hddb but it has no partitions on it.

I am thinking of using it as extra harddrive storage space, but what kind of partitions should I have on it? Primary? extended? should it be ext2, ext3? Fat32? NTFS? what is the difference between all these? I have no idea!

---

### Post by NeghVar on 2006-04-06
If you are dual booting with Windows and want to use it as a spre drive for both fat. Linux currently can not reliably write to NTFS so avoid that right out. 

Ext 3 is probably your best option if it is only linux running. It is more effcient than fat and it is a native linux fs so you won't have many issues and if anything goes wrong you are most likely to get help here on that as most use it.

---

### Post by taurus on 2006-04-06
On your second harddrive, you can have up to 4 primary partitions and if you want more, then you need to convert one of those primaries to logical and then create as many extended partitions as you wish.  SInce you plan to use it for backup in Ubuntu only, I recommand you create one primary, taking all the space of your harddrive, and format it as ext3.  BUT if you plan to share that second harddrive with Windows, then better format it as fat32 so both Ubuntu and Windows can read it.  In other words, if you only have Ubuntu on that machine, then do ext3 but if you want to share it with Windows, then do fat32...

If you are not sure how to partition and format your second harddrive, /dev/hdb, let me know and I can type out the steps!!!

---

### Post by ncappel1 on 2006-04-06
I don't have windows on my computer anymore, so I think I will convert the extra drive into an ext3 partition. 

I was planning on using gparted (though I can't say I have any experience with it). taurus, what steps do you suggest taking?

---

### Post by Sutekh on 2006-04-06
What do you plan to put on the second disc?

Would there by any advantage to having more than one partition?  (I know that might be a difficult question to answer now, but think about what you are going to use it for, you might decide that two partitions could be beneficial)

If not just use GParted to turn it into one large Primary ext3 partition.  GParted is pretty easy to use.  Plus since its a brand new hard drive with nothing on it, you can't really go wrong.

You can check out the GParted web page for some screenshots and documentation, but you'll find yourself learning pretty quick.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by taurus on 2006-04-06
[QUOTE=ncappel1]taurus, what steps do you suggest taking?[/QUOTE]
Okay.  You first need to create a partition and you can do what with fdisk.  Open a terminal with Applications -> Accessories -> Terminal and type
```

sudo fdisk /dev/hdb

```
If you want to see the list of all the commands you can use in fdisk, just hit letter l.  Since you want to create a partition, hit n (for new).  Then, hit p (for primary) and 1 for the first one.  Give it all the space.  Now, you need to convert that to a Linux ID by hitting t and number 83.  Save it and exit with w.  This would put you back to the prompt.  You now need to format it as ext3 by
```

sudo mke2fs -j /dev/hdb1

```
Wait for it to finish and create a mount point and edit your /etc/fstab so it would be mounted automatically upon boot.  
```

sudo mkdir /media/backup
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab

```
Add this line to the end of /etc/fstab and save it...  
```

/dev/hdb1  /media/backup  ext3  defaults  1  1

```
Then, type these two commands at the prompt to mount it and list all the drives on your machine...
```

sudo mount -a
df -h

```
Let me know how it turns out.

---

### Post by ncappel1 on 2006-04-06
I really don't have any uses planned out for it, the drive is actually the original one that came in my computer about 6 years ago. Since then, a new hardrive has gone into it, a 120 gb one. I wiped the whole computer clean to install ubuntu. it only installed on the 120gb drive, the original 5gb drive is now the slave, but has been left unformatted. I am not even close to using up all 120 gb of space on the main drive. I really just wanted to use the drive instead of letting it sit there and do nothing. Is there a more practical way to set up the partitions so as to let it contribute something more than just extra space? 

I have heard that some people use small secondary drives to hold their swap partitions, or their /home directory, and the like. Is there a practical reason for this? or will it just bog up and slow down my already out of shape computer even more?

---

### Post by taurus on 2006-04-06
The reason some people use a second drive as their /home is because if the first harddrive dies, then they don't loose all their personal data since /home is on a seperate drive!!!  So, you can either make your small second harddrive as an additional swap space if you choose (then you would have a lot swap partition) or you can use it to store some personal stuff...  It's really up to you what you want to do with it.  Since it's only 5GB, I don't know if you want to place /home on it since you could run out of space soon if you have pictures, movies, mp3s, etc. in your home directory.

---

### Post by Sutekh on 2006-04-06
I have /home on a different partition but not a different disc.  It could actually make things faster to do this.  If you don't already have /home on a separate partition, perhaps you could think of moving it to one on the second disc.

Otherwise, you could make smaller partitions for different things.  Maybe a backup partition, or a multimedia partition, a partition for testing out other versions of Ubuntu or other distributions.  I like this sort of modularity.  Its up to you.

---

### Post by ncappel1 on 2006-04-08
I tried it out, and it worked perfectly! I actually used Gparted to make the partitions, just to use it for the first time, and then I followed the code Taurus so kindly posted to mount and set it up. I had no idea it was going to be this easy. I remember how much of a hassle it was to do with windows. I am continually impressed by how easy Ubuntu makes things. Thanks to all. 

One final question about backing things up. if I backup just my /home folder, if, for example my computer got so broken that I needed to reinstall ubuntu (or upgraded to dapper), if I overwrote the backup /home to the filesystem, would that reload the extra programs and settings Ive already installed? ie. abiword, quodlibet, firefox 1.5,  automatix, or are the places where these are installed different from the /home folder?

---

### Post by mistab1034 on 2006-04-08
Your /home directory does not contain the extra program files you installed, but it may have some of your personal settings from those programs. For example with firefox you should have a ~/.firefox or ~/.mozilla/firefox directory which contains things like your bookmarks, extentions, and history. So in the case of a reinstall of your system and you restore your /home directory from your backup all your firefox settings will be restored as well.

If you want to make sure your extra programs are backed up your going to have to backup a few other directories along with /home. For some more information on how the Linux directory tree works and where all the files from your extra programs are I suggest this document:
[http://www.tldp.org/LDP/sag/html/sag.html#DIR-TREE-OVERVIEW]("http://www.tldp.org/LDP/sag/html/sag.html#DIR-TREE-OVERVIEW")

---

