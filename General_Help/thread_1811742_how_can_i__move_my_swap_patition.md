---
title: "how can i  move my swap patition?"
date: 2011-07-25
forum: General Help
---

### Post by F.G. on 2011-07-25
hi folks,

I'm currently doing a bunch of work on windows xp need to resize a ntfs partition (make it bigger). the problem is that it's wedged between the beginning of the disk and my swap partition.

so, i figure i can boot up with something like knoppix (i think it doesn't use a swap) or backtrack in forensic mode and then use gparted to move my swap partition into the space next to it (it isn't next to my root filesystem, so that should be ok).

however, I remember reading (in a post that i can't seem to find now) that if you move a swap partition your main filesystem will no longer be able to use it (as i guess memory references and offsets etc will all be wrong, although presumably all it needs to know is where the swap partition is).  so, is this true, and if so how can the swap be re-associated? 
so, any thoughts? i'm guessing that there's a ID or reference that needs to be changed somewhere, though i don't know what it is.

this isn't particularly urgent, though i do want to figure out how to do it, thanks for any help.

f.g.

---

### Post by seawolf167 on 2011-07-25
Boot up off a Ubuntu LiveCD (or GParted LiveCD). Once booted, delete your swap partition and resize/move/do whatever you wanted to on your other partitions. Once that is set and you have your unallocated space where you want it and of the size you want it (for swap space), create a partition there and format it as type "linux-swap".

Once all the partition changes have been made and you are booted back into Ubuntu, you'll need to activate the swap partition by editing the /etc/fstab file

First, find the UUID of the swap partition from 

```
sudo blkid
```then open /etc/fstab for editing

```
gksu gparted /etc/fstab
```and change the existing swap partition UUID to the new swap partition UUID. Save the file and close.

You are all set now. Note that if you want to enable the swap use during hibernation you'll have a couple more steps.

EDIT: Made a mistake in typing the above command it should read

```
gksu gedit /etc/fstab
```**NOT**

```
gksu gparted /etc/fstab
```Thanks for Catkiller for catching this!

---

### Post by CatKiller on 2011-07-25
> **seawolf167 said:**
> 
```
gksu gparted /etc/fstab
```and change the existing swap partition UUID to the new swap partition UUID. Save the file and close.

I think you mean ```
gksudo gedit /etc/fstab
``` :)

---

### Post by seawolf167 on 2011-07-25
Yes you are correct - thanks for catching that!

---

### Post by F.G. on 2011-07-25
Thanks seawolf167, that solution is exactly what i was looking for and has worked perfectly.
although now, if I try to resize the ntfs partition i seem to get an error and the operation is cancelled. i've got a bunch of empty space next to it, so guess i'm going to look for a .exe program and see if i can do it from inside windows (if that's possible).

---

### Post by seawolf167 on 2011-07-25
> **F.G. said:**
> Thanks seawolf167, that solution is exactly what i was looking for and has worked perfectly.
although now, if I try to resize the ntfs partition i seem to get an error and the operation is cancelled. i've got a bunch of empty space next to it, so guess i'm going to look for a .exe program and see if i can do it from inside windows (if that's possible).

Yea - to resize an NTFS formatted parition you'll want to use the built in Windows partition editor. If you start your computer, then right click "my computer" select "manage" then select "disk management" you will be able to use the Windows partition editor to manage their partitions. Be careful since Windows does not recognize ext/swap partitions.

---

