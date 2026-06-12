---
title: "How to acces EXT4 from Windows"
date: 2010-05-30
forum: General Help
---

### Post by snowed on 2010-05-30
I am using mainly Ubuntu 10.4 but sometimes have to switch to Windows but want to have file accessible. Is it possible somehow. If yea please give me advise.

---

### Post by ibuclaw on 2010-05-30
Windows does not support Linux Ext filesystems. If you need to share data between the two, keep it on an NTFS/FAT filesystem am afraid.

Usually pendrives come in handy right about now... :)

---

### Post by benerivo on 2010-05-30
There's some software that allows windows to read/write ext filesystems, but none of them can do ext4 properly. This howto suggests that one piece of software works for ext4, but with read only. I used to do it with ext3 partitions all the time, but i wouldn't want to risk losing any of my files on ext4.

[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

---

### Post by jerome1232 on 2010-05-30
You can access ext2/3, but not 4.

Generally if you have data you want shared, ie media, keep it on fat or ntfs since linux can work with them well.


I personally keep a seperate data partition, ntfs. Make my ~/Pictures, ~/Videos, ~/Music, ~/Downloads, and ~/Documents symnlinks to repsective folders on the data partition so it's fairly seamless.

---

### Post by Bad.Andy on 2010-05-30
If your hardware/patience can handle it, try running your existing Ubuntu installation from within Windows using VirtualBox. You can then share folders between the two pretty easily.

Another alternative is to use a free service like dropbox.com to sync your data (hint, you can use links to sync files that are stored outside your dropbox folder).

Guides exist for both, let me know if you need any help finding them.

---

### Post by ajgreeny on 2010-05-30
> **Bad.Andy said:**
> If your hardware/patience can handle it, try running your existing Ubuntu installation from within Windows using VirtualBox. You can then share folders between the two pretty easily.

Another alternative is to use a free service like dropbox.com to sync your data (hint, you can use links to sync files that are stored outside your dropbox folder).

Guides exist for both, let me know if you need any help finding them.
That seems a roundabout way to do something which is most simply achieved with a separate data partition, as suggested by jerome1232.

I agree that is the way to go.

---

### Post by N8N on 2010-05-30
> **ajgreeny said:**
> That seems a roundabout way to do something which is most simply achieved with a separate data partition, as suggested by jerome1232.

I agree that is the way to go.

but if you make your data partitions NTFS, couldn't then any Linux user with access to that machine be able to access them and worse yet write over them?

Not an issue if you are the only user on your system though...

I would def. be interested to hear if anyone has any info on a utility that will properly handle reading ext3/4 partitions from Windows as I am in pretty much the same situation as the OP.  Now I have set up SAMBA shares so I can access the files from any *other* PC on my network, but if I want to use the computer at my desk but need to be in Windows for some reason and need a personal file, I'm screwed.

---

### Post by jerome1232 on 2010-05-30
Anyone with physical access to your machine can access any file anyways. (you can pass options to the kernel at boot time that will give you root access with no password, if you boot ubuntu into rescue mode you get root access with no password, if you boot a live cd you get root access with no password)

edit: I actually don't see how ntfs is any less secure than a linux filesystem actually (less flexible certainly) seeing as only root can mount, therefore only users in the admin group can modify it's permissions. Furthermore only admin users can edit /etc/fstab. So just make sure you set permissions on it as you see fit.


If it's privacy/security you want then you would need to encrypt the partition using truecrypt and always lock it when your done using it.

---

### Post by ShadowPuppet on 2010-06-08
A bit of googling here and there hasn't answered a question of mine: Is there any way currently for Windows (specifically 7) to write (the more important of the read/write question) to ext4?

---

### Post by JoelOl75 on 2010-06-08
Your best bet is:

Use a Fat32 formatted usb key and copy the files from Linux onto the key.  Then get to them from Windows or...

Install another hard drive and format it NTFS.  Set up a moint point in your fstab file for the drive.  Now both OS's can use it.  You can also make room (shrink) a partition on your current drive and make a small fat32 or NTFS partition there.  

Or...  Just copy the file (in Linux) to your Windows partition.  Unfortunately you can't do it the other way around, but Linux can see your Windows partition.

---

### Post by Placinta on 2010-06-13
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

---

