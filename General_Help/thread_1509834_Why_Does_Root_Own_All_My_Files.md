---
title: "Why Does Root Own All My Files?"
date: 2010-06-14
forum: General Help
---

### Post by EoRaptor013 on 2010-06-14
I was trying to extract a tar file to my home directory. The operation failed because I didn't have permission! I did an ls -Al and discovered that all my folders and files are owned by root, and the group is plugdev. 

I am a member of the plugdev group, and (ducking for cover) a member of the root group. Nevertheless, I seem not to have the necessary permissions on various folders and groups. I even went so far as to sudo chown individual files, directories, and directory trees. Using the -v switch, chown reports changing all the files. But, entering ls -Al, shows nothing was actually changed. 

I don't see in the new release notes that this is a new behaviour. On the other hand, I often miss the obvious. 

What's going on? Or, at least, point me to the correct documentation, please. 

Thanks.

---

### Post by ubunterooster on 2010-06-14
try ```
gksu nautilus
```go to your home right-click and select properties>permissions.

---

### Post by EoRaptor013 on 2010-06-14
Been there, done that, didn't work. When I right click for properties, then click on the dropdown list for either owner or group, the values _return_ to the original owner (root), group (plugdev). You don't even get to click the OK button before the dropdown list values change. 

And, as noted elsewhere, there are many things I can't do **in my own home directory**!

This just makes no sense to me. But, thank you for responding.

Randy

---

### Post by James78 on 2010-06-14
Did you enable the recursive flag?

```
sudo chown -R user:user /home/user
```

---

### Post by EoRaptor013 on 2010-06-14
Yep. Actual command for test purposes:

sudo chown -Rv myusername:myusername ~./Pictures

The verbose switch showed chown changing both folder and file permissions. But, when I do an ls, or use a file manager,  the files are still owned by root, and group plugdev. 

I've been trying to run wine, but can't because I don't own the .wine subdirectory in my own bleeding home directory!

As you can probably tell, I'm getting agitated about this!

Thanks. 

Randy

---

### Post by dtfinch on 2010-06-14
Your home directory wouldn't happen to be on a vfat/fat32 partition, or on a removable drive, would it?

---

### Post by aysiu on 2010-06-14
[QUOTE=EoRaptor013;9462374]Yep. Actual command for test purposes:

sudo chown -Rv myusername:myusername ~./Pictures/QUOTE] Why is there a . in there?

It should be *sudo chown -R randy:randy ~/Pictures*

But really to be safe, you should just *chown* the entire user home directory: ```
sudo chown -R randy:randy /home/randy
```

---

### Post by EoRaptor013 on 2010-06-14
> **dtfinch said:**
> Your home directory wouldn't happen to be on a vfat/fat32 partition, or on a removable drive, would it?
Hmm... 

Funny you should mention that. I dual boot Win7 and Lynx. During install, I created 4 partitions: Win7 (ntfs); Linux (ext4); SWAP; and DATA. I sized both Win7 and Linux at 40Gb, and allocated the remainder (minus SWAP) to DATA. I then mounted DATA at /home/myusername. Oh, yes, DATA is formatted NTFS, not vfat or fat32. 

My thinking was that I could access all the files in my home directory from either Win7 or Lynx. Was this, perhaps, bad thinking? Somehow I'm getting that cold, hard, feeling in my gut...

Thanks.

Randy

---

### Post by EoRaptor013 on 2010-06-14
> **aysiu said:**
> [QUOTE=EoRaptor013;9462374]Yep. Actual command for test purposes:

sudo chown -Rv myusername:myusername ~./Pictures/QUOTE] Why is there a . in there?

It should be *sudo chown -R randy:randy ~/Pictures*

But really to be safe, you should just *chown* the entire user home directory: ```
sudo chown -R randy:randy /home/randy
```

I was just testing. Didn't want to take a chance on munging something up. What's in my Pictures directory is expendable. 

In any event, I just tried (from the home directory) sudo chown -Rv myUserName:myUserName ./myUserName/Pictures. As previously, the verbose listing shows files and folders being changed as I would want. But when the dust settles, nothing has actually been changed. I really don't understand why chown isn't throwing some kind of error if nothing is actually changing.

Thanks.

Randy

---

### Post by aysiu on 2010-06-14
> **EoRaptor013 said:**
> Hmm... 

Funny you should mention that. I dual boot Win7 and Lynx. During install, I created 4 partitions: Win7 (ntfs); Linux (ext4); SWAP; and DATA. I sized both Win7 and Linux at 40Gb, and allocated the remainder (minus SWAP) to DATA. I then mounted DATA at /home/myusername. Oh, yes, DATA is formatted NTFS, not vfat or fat32. 

My thinking was that I could access all the files in my home directory from either Win7 or Lynx. Was this, perhaps, bad thinking? Somehow I'm getting that cold, hard, feeling in my gut...

Thanks.

Randy Your /home/username directory cannot be NTFS or FAT32. It has to be some kind of Linux filesystem (Ext3, Ext4). That's why your permissions are all screwed up probably.

---

### Post by EoRaptor013 on 2010-06-15
aysiu said:
Your /home/username directory cannot be NTFS or FAT32. It has to be some kind of Linux filesystem (Ext3, Ext4). That's why your permissions are all screwed up probably.

Rage! Thunder! Sturm and drang! It seemed like a good idea at the time. 

Two questions: Would it be possible to change the privileges at mount time by editing fstab? Second, how might I move my home directory to the Linux partition? From there, I could then mount the DATA partition as a subdirectory under my Linux partition home... But then, all my Win7 links will be screwed. I REALLY don't want to reinstall all my Win7 apps!

Oh well, no rest for the weary. But, thank you for clearing that up for me.

Randy

---

### Post by aysiu on 2010-06-15
In order for Linux to function correctly, the configuration files in the user directory have to be on a Linux filesystem. It's okay if your Pictures or Music folders are symlinks to an NTFS partition, but the entire /home/username directory cannot be an NTFS partition.

---

### Post by The Cog on 2010-06-15
> **EoRaptor013 said:**
> Two questions: Would it be possible to change the privileges at mount time by editing fstab? Second, how might I move my home directory to the Linux partition? From there, I could then mount the DATA partition as a subdirectory under my Linux partition home... 
As long as your NTFS partition is mounted to /home then you cannot make the proper home directory for yourself. 

If you are comfortable doing this, then you can boot the live CD and "try ubuntu", mount the ext4 partition and create your home folder, setting the user and group IDs to 1000. Then edit /etc/fstab and remove the line that mounts the ntfs partition to /home. You can make a new mount point for it later.

If that's too hard, you might be better off just reinstalling. Feel free to mount the NTFS partition, but putting it somewhere like /mnt/windows would be good. Don't mount it anywhere ti would interfere with the normal Linux filesystem.

Once the ntfs partition is mounted somewhere safe, you can symlink into it like aysiu sys.

---

