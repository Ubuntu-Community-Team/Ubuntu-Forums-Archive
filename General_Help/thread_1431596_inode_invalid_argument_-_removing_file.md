---
title: "inode invalid argument - removing file"
date: 2010-03-16
forum: General Help
---

### Post by EarthBoundMsfit on 2010-03-16
I am trying to remove a file off of my external that got corrupted. The file is only corrupted not the entire drive. I failed to remove it with the "rm -f" command. Then through some searching I stumbled upon this thread > [http://ubuntuforums.org/showthread.php?t=456714]("http://http://ubuntuforums.org/showthread.php?t=456714") which talked about removing it with an inode number. I thought all my problems were solved! However, to my dismay i got an error wile using the command 
```
find . -inum [inode-number] -exec rm -i {} \; 
```I placed my inode-number in there which happens to be 12593. What i get in return is this.
```
find: invalid argument `-exec' to `-inum'
```I was wondering if anyone could possibly tell me what I am doing incorrectly. I have tried to copy and paste it into the terminal and I have typed it in manually, however I get the same error. 
Any information would be appreciated. I am running in the Ubuntu 9.10 64-bit.

---

### Post by prodigy_ on 2010-03-16
Err... What's wrong with just using fsck? (If the drive is NTFS-formatted, you should use chkdsk from Windows somehow.)

---

### Post by EarthBoundMsfit on 2010-03-16
I am unsure of "fsck" command and how to use it. I looked up man on it and it does not seem to be able to repair a single file it looks like it. I just want to remove the file no need to repair it. I have another copy of it. I just want it gone.

---

### Post by srs5694 on 2010-03-16
If one inode is damaged, chances are good more are damaged, too. Thus, running a full fsck on the filesystem is a good idea.

---

### Post by prodigy_ on 2010-03-17
Well, fsck is a Linux utility that checks HDD partitions for errors. It's similar to Windows chkdsk. And there's a very good chance that you'll be able to delete this file normally after running it. So my recommendations stay: use fsck if your external HDD isn't NTFS-formatted, or use Windows chkdsk if it's NTFS. Use ```
fdisk -l
``` command to identify the filesystem if you're unsure.

One important thing - **the partition must be unmounted when you run fsck on it**. If you're unsure how to unmount a partition, post output of ```
mount
``` command.

---

### Post by EarthBoundMsfit on 2010-03-17
Thanks for all the help fellas. It is an ntfs partition, I think I am just gonna copy everything over and format it with ext4. All your information was a major help, but I thing I am just gonna get rid of this ntfs partition and become full linux! 

Your help is greatly appricated! And I fell welcome here in the forums. I am glad I join this community and I will be glad as soon as I can help out others as much as you have helped me.

Again, thanks a ton!

---

