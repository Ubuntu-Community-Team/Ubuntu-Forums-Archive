---
title: "NTFS read write and permissions issue  ubuntu 11.10"
date: 2011-11-21
forum: General Help
---

### Post by xigen on 2011-11-21
I just got an external drive and formatted it in NTFS.  The HD is in a two bay hotswap drive (thermalake blac x)   with a usb connector to my linux box.  

Unfortunately, when I try to copy files from my system to the NTFS drive I get permissions errors (cannot create folder).

I try $gksudo nautilus 
and attempt to change the permissions only to see the entries revert to a previous state.


ntfs-3g libntfs-3g75  
are both installed on my system.

How do I go about getting the new drive to be accessible to my linux box?

Cheers,

MW

---

### Post by Mark Phelps on 2011-11-21
Unfortunately, if this is a dual-drive bay, it's more likely to be driver problems. I had a similar problem with a USB 3.0 drive bay. It frequently wouldn't mount the drive, and when it did, it would unmount during file transfers.

Was only able to fix this in Windows because only there, was I able to find both updated firmware and updated drivers.

---

### Post by xigen on 2011-11-21
OK.   Well I have a single drive bay I could try.  

Let's see if that works.

I have attached some pictures to clarify.  The NTFS drive is 'seen' however, I am having trouble with the write function and creating folders on the NTFS drive,  my ext3 drive works just fine in the dual drive bay. 

Cheers,
MW

---

### Post by xigen on 2011-11-23
Strange.  It started to work.  I have no idea what I did to get it to work.

My actions:
- I closed firefox
- I may have (*not sure) turned off/on the power to the drive bay device.

It looks like I am closer to getting this solved.  

Chers,

MW

---

### Post by steeetu on 2012-01-06
get rid of ntfsprog and make sure you have ntfs3 if that doesnt work run error check in disk utility. worked for me. 11.10

---

