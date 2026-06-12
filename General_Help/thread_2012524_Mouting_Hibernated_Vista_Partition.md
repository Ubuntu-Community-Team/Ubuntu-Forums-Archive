---
title: "Mouting Hibernated Vista Partition?"
date: 2012-06-29
forum: General Help
---

### Post by cookingmama on 2012-06-29
Hello, I just joined and this is my first post, so I apologize if this the wrong place to post this question.

Earlier this week, my Vista laptop would not boot from hibernation. After trying everything I could, I gave up as I could not do a re-install of Vista. When looking for a way to recover my files, I came across Knoppix(?) and was able to recover the really important data I needed, but I was not able to transfer over my profile folder (about 25GB's) with all of my stuff. 

Anyway, since I still needed to use a computer, and I had kinda liked using Knoppix, I decided to go ahead and install Ubuntu (64-bit) on a partition of the some of remaining hard drive space I had. On a side note, I have been quite impressed with Ubuntu and the performance is like a completely new computer.

So now, I want to recover my Vista user profile and transfer it to my external hard drive so I can reformat the hard drive. However, when I try to access the "OS" under Devices, I get this error message:


UNABLE TO MOUNT OS

Error mounting: mount exited with exit code 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /media/OS


I am very new to Linux and really do not how to mount the OS so I can access my files. Any help would be appreciated. Thank you!

EDIT:
I should mention that when I try:

mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /media/OS  
or
mount -t ntfs-3g -o ro /dev/sda4 /media/OS

I get the message:
mount: only root can do that

Which I don't really understand (again, I'm really new to Linux).

---

### Post by Mark Phelps on 2012-06-29
Linux has real problems trying to mount NTFS partitions that are in an odd state (like hibernation) or have corrupted filesystems.  I don't believe there is any way to force it to mount -- without risking serious corruption to the filesystem.

What MIGHT work, is if you download Minitool Partition Wizard Boot CD, burn that to CD, and boot from that.  That is a free Windows partitioning tool and it might be able to reset the NTFS partition so you can mount it.

---

### Post by cookingmama on 2012-06-29
Thank you for your reply. I tried the program, but did not know how to the unmount the partition. Again, all I want to do is to be able to access the OS and copy over my profile to my external. So if I can access the partition in read-only mode, that would be fine.

---

### Post by cryptotheslow on 2012-06-29
> **cookingmama said:**
> 
EDIT:
I should mention that when I try:

mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /media/OS  
or
mount -t ntfs-3g -o ro /dev/sda4 /media/OS

I get the message:
mount: only root can do that

Which I don't really understand (again, I'm really new to Linux).


That message means you require administrative privileges to carry out the action - so precede the command with sudo

i.e.
```

sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /media/OS  

or

sudo mount -t ntfs-3g -o ro /dev/sda4 /media/OS

```

When prompted enter your password.

Because it is requiring admin privilege to mount you may find you cannot access the files in /media/OS using the file browser.

If that happens open the file browser with admin privileges using:
```
gksu nautilus
```

---

### Post by spjackson on 2012-06-29
> **cookingmama said:**
> 
mount -t ntfs-3g -o ro /dev/sda4 /media/OS

I get the message:
mount: only root can do that

Which I don't really understand (again, I'm really new to Linux).
It means that you need to act as user 'root' by using sudo, i.e.

sudo mount -t ntfs-3g -o ro /dev/sda4 /media/OS

---

### Post by cookingmama on 2012-06-29
> **cryptotheslow said:**
> That message means you require administrative privileges to carry out the action - so precede the command with sudo

i.e.
```

sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /media/OS  

or

sudo mount -t ntfs-3g -o ro /dev/sda4 /media/OS

```When prompted enter your password.

Because it is requiring admin privilege to mount you may find you cannot access the files in /media/OS using the file browser.

If that happens open the file browser with admin privileges using:
```
gksu nautilus
```

Okay, so I am not exactly sure what happened when I entered this (it gave me an error I think), but I somehow was able to access my files! Thank you so much! And thank you to everyone else who helped.

---

