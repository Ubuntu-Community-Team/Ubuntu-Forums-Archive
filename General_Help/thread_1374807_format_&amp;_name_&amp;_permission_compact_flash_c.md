---
title: "format &amp; name &amp; permission compact flash card"
date: 2010-01-07
forum: General Help
---

### Post by audiomick on 2010-01-07
Hallo.
I've run up against a wall (again);)

I have a compact flash card with a key file on it. I need to change the permissions so that only I (i.e. the user me = mick) can rwx it.

The card was fat16, I have reformatted with gparted to ext2 so the permissions stick.

The card now belongs to root, which I will have to change with "sudo chown", and then set the permissions with "chmod". I think I can manage that.

What is stopping me is that I want to give the card a name. At the moment, it shows up with what appears to be the UUID. I have tried naming it with "gksu nautilus", but it wont let me. Says the card is in use. If I unmount it, it disappears from the root instance of nautilus.

The card shows up in "fdisk -l" as /dev/sdd, the partition as /dev/sdd1

Can someone tell me which command I need to give the card a name?

---

### Post by viralmeme on 2010-01-07
> **audiomick said:**
> .. Can someone tell me which command I need to give the card a name?

*[I]**Note***: don't try this on the disks that have data. Labelling them can destroy it.[/I]

[http://www.virtualhelp.me/component/content/article/39-linux/90-mount-disks-with-uuid-or-label](http://www.virtualhelp.me/component/content/article/39-linux/90-mount-disks-with-uuid-or-label)

---

### Post by audiomick on 2010-01-07
@ymitchell

Thanks for the warning, but don't worry. I have the relevant file copied off to somewhere else for the time being. At the moment the card is empty, until I get it set up the way I want it. Can you give me a clue how to go ahead?

---

### Post by todak on 2010-01-07
Use the Disk Utility located in the System >Administration menu. Click on the partition of the disk you want to label and unmount it. Then on the right side of the window, you will find a box to label the drive with a descriptive name. After labeling the disk, mount it and it will show on your desktop with the new name, ready for use.

---

### Post by audiomick on 2010-01-07
All done.
Thank you very much todak. I wouldn't have thought of that, as I have never used the disk utility before. ;)

---

### Post by todak on 2010-01-07
> **audiomick said:**
> All done.
Thank you very much todak. I wouldn't have thought of that, as I have never used the disk utility before. ;)

You are welcome. As you probably discovered, you had to select a partition to unmount/mount and write a label, not the root of the drive! My brain had it right, but my fingers refused to type the info in the correct order! :D

---

