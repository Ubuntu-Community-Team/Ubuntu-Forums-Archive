---
title: "Editing fstab difficulty"
date: 2011-01-11
forum: General Help
---

### Post by MAJOR[SWE] on 2011-01-11
I've researched fstab configuration for a while now and cannot seem to fix these two problems I'm having with mounting. In attempting to solve the first problem I created a second problem.

Here's the necessary information:

```
/dev/sda5: UUID="961e53b4-a11d-4344-81fd-0140392db1f9" TYPE="ext4" 
/dev/sda6: UUID="8d3dd063-1aa5-4728-8a9d-46344b7dd1c6" TYPE="swap" 
/dev/mapper/truecrypt1: UUID="b102c78d-db6f-417b-88ae-72eb81fbe17f" TYPE="ext3"
``````
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda6 during installation
UUID=961e53b4-a11d-4344-81fd-0140392db1f9  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda7 during installation
UUID=95313b71-8861-434b-a601-8041360536f3  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/My Passport     ext4  defaults               0  0  
/dev/sdb1                                  /media/sdb1     ext4  defaults                  0  0  
/dev/sdb1                                  /media/truecrypt1 ext3 rw,user,noauto           0  0   
```My first problem was receiving mounting errors on boot regarding the two first sdb1 mounts (My Passport and sdb1). Don't know how they came to be but the only mount that I want from sdb1 is the truecrypt1 (although not on boot). The problem was that after GRUB I got an error saying that it couldn't mount /media/My Passport and /media/sdb1...hit skip for both of them and everything goes smooth. However, I don't want that on boot so I proceeded to edit fstab. In doing so I created a reoccurring error pertaining to my truecrypt mount. I can mount it and read/write but cannot unmount using any method. The last line of my fstab (*/dev/sdb1 /media/truecrypt1 ext3 rw,user,noauto 0  0*) was not there at the time, so I have no idea how I was able to mount and r/w in the past. I added that line to the end of fstab and now I get this error during unmount:

[IMG]http://img835.imageshack.us/img835/8091/mounterror.jpg[/IMG]

I am unable to properly remove the empty/obsolete mount points (/media/My Passport and /media/sdb1) from fstab and restore the /media/truecrypt1 to a working line. Any help with this is greatly appreciated!

*Also, for future editing purposes: the column alignment in fstab is difficult to manage since some mount points and information are so long that they shift the vertical alignment out of order by a few spaces. What would be a good solution?

---

### Post by Quackers on 2011-01-11
I don't know about truecrypt or how it works, but I notice a couple of things from your code quotes.
In the first your /root is on /dev/sda5 and your swap is on /dev/sda6
In the second your /root is on /dev/sda6 and your swap is on /dev/sda7 AND using a different UUID

---

### Post by MAJOR[SWE] on 2011-01-11
That is strange, I didn't notice the obvious difference. I haven't noticed any problems with that though. Could it have an effect on my sdb1?

Let's just imagine the partition isn't encrypted and lets treat the line as if it were a normal one. I'm pretty sure it's just some minor error in my editing of fstab. For example, before I added the last line I got an error that read:
[I]
'Line 14 in fstab is bad   Unable to unmount truecrypt1 umount: /media/truecrypt1 not in the [COLOR=Black]fstab[/COLOR] (and you are not root)'[/I]

I edited line 14 so that the dump and fsck values (0 0) were vertically aligned with the values of other partitions. They were off by two spaces and after editing that problem went away. I believe my error regarding /media/truecrypt1 is similar.

---

### Post by Quackers on 2011-01-11
I'm not familiar enough with your type of setup to comment. 
All I would say is that either your /root is on sda5 or sda6 but it can't be on both!
The same is true of your swap partition.
It would be a good idea to check what is on where and also their UUID numbers.
Maybe in gparted? Right-click each partition and select "information". The details are in there.

---

### Post by MAJOR[SWE] on 2011-01-11
gparted confirms bklid. Root is on sda5 (same UUID) and swap is on sda6 (same UUID). There is no sda7.

If fstab does not correspond to what bklid reports then I'm starting to think I royally screwed my fstab. Unfortunately I forgot to make a backup before I edited fstab and received the error

> *'Line 14 in fstab is bad   Unable to unmount truecrypt1 umount: /media/truecrypt1 not in the [COLOR=Black]fstab[/COLOR] (and you are not root)'*I do have a backup from before the next step, that is, before i added the /media/truecrypt1 line to the end of fstab. It looked like this:

```
**Code:**           # /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc                                       /proc           proc  nodev,noexec,nosuid       0  0   
# / was on /dev/sda6 during installation 
UUID=961e53b4-a11d-4344-81fd-0140392db1f9  /               ext4  errors=remount-ro         0  1   
# swap was on /dev/sda7 during installation 
UUID=95313b71-8861-434b-a601-8041360536f3  none            swap  sw                        0  0   
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0   
/dev/sdb1                                  /media/My Passport  ext4  defaults                  0  0   
/dev/sdb1                                  /media/sdb1     ext4  defaults                  0  0 
```I'm not experiencing any overt problems with sda, only safely dismounting sdb1.

---

### Post by Quackers on 2011-01-11
If that's the backup, it references sda6 for /root and sda7 for swap, but you said sda7 doesn't exist in gparted?

---

### Post by MAJOR[SWE] on 2011-01-11
Exactly, no reference to sda7 anywhere. I edited my partitions a few days ago where I think I deleted my swap and then created a new one. However, the error, *'Line 14 in fstab is bad   Unable to unmount truecrypt1 umount: /media/truecrypt1 not in the [COLOR=Black]fstab[/COLOR] (and you are not root)', *started occurring before that..like a week ago.

In my attempt to fix that by adding the last line seen in my last edit of fstab I think I screwed up somewhere in writing out the line. I feel like it's something minor, like the alignment of that line not matching the others. Notice "/media/truecrypt1" forces "ext3" and the options to shift to the right a little and thus not matching the columns of the other filesystems.

Since the sdb1 truecrypt volume is mounted and I have rw access...there has to be a way to --force dismount it or something.

---

