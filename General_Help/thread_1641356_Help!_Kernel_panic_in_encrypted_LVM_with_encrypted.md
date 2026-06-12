---
title: "Help! Kernel panic in encrypted LVM with encrypted home"
date: 2010-12-08
forum: General Help
---

### Post by ruipedroca on 2010-12-08
I screwed up trying to install a new kernel :(
Now, when I try to boot up, it says:
kernel panic not syncing VFS unable to mount root fs on unknown block

My system:
-encrypted LVM with encrypted home 
-10.04 ubuntu system

What's the easiest/fastest way recover the documents on my encrypted home folder?

I have the home folder encryption passphrase.
I just want to recover and backup those documents, even if after that I have to reinstall the whole system.

I have a live CD and also another 10.04 system on a second computer.
I've managed to mount the hard drive in this second system and see everything on it, except the contents of the user home folder (Private).
Everything I see on the internet is about encrypted home, but not top of a LVM encrypted.

Can somebody please help? :o

---

### Post by iponeverything on 2010-12-08
did you try booting the previous kernel from the grub menu..

-- any special reason for encrypted home on a LUKS partition, besides just trying to use some of those excess cpu cycles?

---

### Post by ruipedroca on 2010-12-08
> **iponeverything said:**
> did you try booting the previous kernel from the grub menu..
That was my first idea, but I don't knw how.
Please, tell me how to do that as this is grub2 now on 10.04.
Should I manually enter the /boot partition and edit some file?
I've entered /boot and I can see more kernel versions there.

> **iponeverything said:**
> 
-- any special reason for encrypted home on a LUKS partition, besides just trying to use some of those excess cpu cycles?
The reason was I need to share this computer with other persons and wanted to make sure my documents couldn't be accessed.
Now I feel like I should have found another solution for this.

Thanks in advance

---

### Post by ruipedroca on 2010-12-08
Finally, success! :)

In case it helps someone else in the future:


I mounted the hard drive in another system, then entered /boot and edited grub.cfg. 

Here, the only thing I've done was to find the word "timeout" which appeared 6 times and then added 3 (seconds) to the default value (instead of -1 I've put 2, instead of 0 I've put 3, etc). 

Then tried to boot with the hard drive and the option to choose the different kernels appeared; I've just had to choose one of the others.

Now, I'm going to backup ;)

---

