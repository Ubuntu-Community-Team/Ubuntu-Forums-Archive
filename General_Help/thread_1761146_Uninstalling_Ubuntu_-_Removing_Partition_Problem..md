---
title: "Uninstalling Ubuntu - Removing Partition Problem."
date: 2011-05-17
forum: General Help
---

### Post by ExoGenesis91 on 2011-05-17
So, I've been using Ubuntu for about a month now, and despite all it's perks, I've decided it's not for me.

I miss too many of the native Windows programs and getting them to work on it is to taxing for me.

But I'm having a problem uninstalling Ubuntu to allow me to install Windows 7.

I have the W7 disc and I first tried using that, only to release it can't just wipe my drive and I need to "manually" get rid of the Ubuntu partition. However, i can't figure out how to do that. i've been looking for days on Google and other forums etc but found no clue.

I installed the Gnome Partition Editor, but it lets me do nothing with the Ubuntu Partition, and I'm at a complete loss as to what I'm to do.

---

### Post by hhh on 2011-05-17
I thought Windows install discs DID wipe and format drives automatically, but...

The Gnome Partitioner (A.K.A. Gparted), or any other partitioner as far as I'm aware, cannot format a drive that is currently in use. Burn an Ubuntu Live CD if you don't already have one and use Gparted from that in a live session. You'll need to delete the existing partitions and then format the drive to ntfs to install Windows.

More info...
[http://answers.yahoo.com/question/index?qid=20110425143120AAgP91d](http://answers.yahoo.com/question/index?qid=20110425143120AAgP91d)

Also see Ramin15's answer here...
[http://answers.microsoft.com/en-us/windows/forum/windows_7-system/how-do-you-remove-ubuntu-and-grub/42d3f550-bf5f-459d-94ed-4cbadd7c933c](http://answers.microsoft.com/en-us/windows/forum/windows_7-system/how-do-you-remove-ubuntu-and-grub/42d3f550-bf5f-459d-94ed-4cbadd7c933c)

---

