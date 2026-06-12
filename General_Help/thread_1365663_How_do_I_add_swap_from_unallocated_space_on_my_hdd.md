---
title: "How do I add swap from unallocated space on my hdd?"
date: 2009-12-27
forum: General Help
---

### Post by spacesearcher on 2009-12-27
So heres how I screwed it up.
I had a large partition with karmic on it.
I had a smaller partition with Jaunty on it and an extended partition with the swap. I belive that the Karmic was using that swap as well. 

I needed to install window 7 for school so I got rid of the smaller partition with Jaunty on it in doing so I got rid of the swap. 

I now have errors when booting into karmic telling me It cant mount swap. if I wait it eventually starts up but I don't have swap. 

I looked at the partitions in gparted and I have a few gigs of unallocated space in /dev/sda4. How can I format this as swap and tell my system to boot that instead of what it thought the old swap was?

---

### Post by taurus on 2009-12-27
You can create a swap partition with the unallocated space from gparted.  Then, open a terminal and determine the UUID of that new swap partition.

Applications -> Accessories -> Terminal
```
sudo blkid
```
Now, you need to edit /etc/fstab and replace the UUID for the old swap (no longer exist) with the new one.

```
gksudo gedit /etc/fstab
```
Save it and reboot.

---

### Post by lukeiamyourfather on 2009-12-27
The system looks for what partition to use as swap from the file /etc/fstab. You'll need to create a new swap partition with something like GParted and change the swap entry in /etc/fstab to point to the new partition. Cheers!

EDIT: taurus beat me to it.

---

### Post by spacesearcher on 2009-12-27
Thanks! I got it working. I used the live cd because when I tried doing it with out I got weird results when I tried to format the unallocated space. That was much easier than I expected.

---

### Post by dcstar on 2009-12-27
> **taurus said:**
> You can create a swap partition with the unallocated space from gparted.  Then, open a terminal and determine the UUID of that new swap partition.

Applications -> Accessories -> Terminal
```
sudo blkid
```
Now, you need to edit /etc/fstab and replace the UUID for the old swap (no longer exist) with the new one.

```
gksudo gedit /etc/fstab
```
Save it and reboot.

AFAIK there is also a file that needs the new UUID set for Suspend/Hibernation to work - a forum search should provide the details.

---

