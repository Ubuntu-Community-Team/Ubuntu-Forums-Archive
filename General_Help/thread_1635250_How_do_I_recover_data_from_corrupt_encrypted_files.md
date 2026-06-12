---
title: "How do I recover data from corrupt encrypted filesystem"
date: 2010-12-01
forum: General Help
---

### Post by dpinna on 2010-12-01
Hey everyone,

Recently I was forced to hard reset my computer a couple of times (mostly out of frustration) and due to my idiocy i was confronted with the standard Kernel Panic message at bootup. I tried running an fsck from live cd which corrected a bunch of errors but to no avail (as far as getting rid of the Kernel Panic msg). I then tried to mount the filesystem by accessing it from live cd (and later even installed ubuntu on a small leftover partition to get rid of the annoying live cd lag) but it says that I don't have access to my home or root folder. Mounting from command line gave the same issue.

So now to the question. Is there a general procedure to access data in my corrupt filesystem if it is encrypted?

Any help would be immensely helpful....

Daniele

---

### Post by dpinna on 2010-12-04
Addendum: 

Trying to boot from any of the recovery modes fails for the same "kernel panic - unable to sync, killed init" reason

I'm really at a loss here.... I would format everything but there's one particularly important document that I need which I don't have backed up.

Anyone have any clues???

---

### Post by sikander3786 on 2010-12-04
Welcome to the forums :-)

For mounting your encrypted home folder, please see these links.

[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

[https://help.ubuntu.com/community/EncryptedFilesystemHowto3#Encrypted%20Home](https://help.ubuntu.com/community/EncryptedFilesystemHowto3#Encrypted%20Home)

I hope you would be able to recover you data safely.

Good Luck!

---

### Post by dpinna on 2010-12-08
I'm pretty sure I may have just complicaed everything.

Potential Error 1: Instead of using Live CD to follow the tutorials, I flat out installed Ubuntu on a small leftover partition on the laptop. I figured this wouldn't make too much of a difference and allow me to not be lagged by the need to boot off of a cd.

Potential Error 2: All my attempts to mount the encrypted file system were to no avail. I managed to mount -bind the corrupted filesystem but when chroot-ing to it, I kept receiving the "/bin/bash: No such file or directory" message. At this point I committed my potential second mistake.... I rebooted the pc without unmounting. To be correct, my battery was running out and i was afraid that if the computer was going to die it would cause "damage".

After restarting, the corrupted filesystem didn't even appear on the bootup screen anymore.... the filesystem partition wasn't visible anymore fromt he newly created ubuntu partition anymore either. (Before I could at least see the home folder). Running fsck on the corrupted filesystem (i remember it being /dev/sda1) was now giving me superblock errors.

At this point I found forum posts pointing me to RIPLinux.... running it, I used TestDisk hoping to repair my original partition. TestDisk wasn't capable of figuring out the type of /dev/sda1. Which leads me to...

Extremely Probable mistake 3: In an act of frustration, I deleted the new ubuntu partition. The act was mostly justified by my being pissed off for it being in the way when I should have been using the LiveCD all along.

Summary: I have a blank screen on bootup.... RIPLinux tells me that, according to it, my original partition (the one on which the corrupted filesystem was) is unallocated and I have absolutely NO IDEA WHAT TO DO if.... that is..... ANYTHING CAN BE DONE.

I haven't formatted the original partiotion or anything of the sort. I haven't touched the data in any way.... technically, shouldn't it still be there? Shouldn't there still be a block of encrypted data?

Any ideas would be greatly appreciated... otherwise, my idiocy is one for the books and should be used as a model for what NOT to do when your encrypted filesystem goes corrupt.

Cheers... :(

---

### Post by Spyderkid on 2010-12-08
If you want to I would say use a cut down live CD like Tiny Core and access the filesystem from there (worked for me)

and you don't have to install tiny core it runs in your RAM (bonus) so you won't have problems with accessing hard drive when you try to boot up 

Just mount the hard drive using the mount key (its very easy)

---

### Post by iponeverything on 2010-12-08
Potential Error 1
Potential Error 2

should not have made made a difference. The fact that partition was on longer showing showing up after hard shutdown, leads me to think that the drive is failing. Booting from live disk Go to: 

"System -> Administration -> Disk Utility" and look at the SMART data for the drive. 

If you manage to see and mount it again, don't chroot. Just cd to mounted partition, find your important data -- and copy it to a flash drive. 

Dirty shutdowns are only an issue if there are un-flushed disk buffers, since nothing was running from the mounted partition at the time of the dirty shutdown there were no un-flushed buffers.

Also, in the future to force a flush type: sync

It may have been fsck that caused you so much grief.

Was the encrypted partition mounted when your fsck on it? If not fsck may have mucked things.

---

### Post by dpinna on 2010-12-08
No.... I made sure I ran fsck only when the partition was unmounted.

I ran disk utility but wasn't capable of mounting.... a look through gparted still gave me the partition as being completely unallocated. 
I rebutted by modifying the partition. I simply set it up as my primary partition with ext4 type (which was what my filesystem was originally).
On reboot with LiveCD I can now see the partion but inside all i have is the Lost+Found folder (with an X on it by the way).

Has my partitioning deleted everything else?

I'm now trying to run photorec from RIPLinux although I doubt it cn get very far since the filesystem is encrypted. If there's a leeson learned here is to never encrypt my filesystem unless I have a regular backup routine setup

---

### Post by iponeverything on 2010-12-08
it should have been mounted (ro)  

fsck probably has no idea how fix an encrypted partition, though that might not keep it from trying.

---

