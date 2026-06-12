---
title: "Something isn't right - 11.10 to 12.04 new install"
date: 2012-07-21
forum: General Help
---

### Post by catnip_X07 on 2012-07-21
Last week had an issue with my 11.10 as it would not recognize any internet connection and a few other operational issued occurred.  Seems to have started after i booted the computer and fdisk started running.  

Anyway, after 3 days of playing with 11.10 to get it back, i decided on a fresh new install of 12.04, only I think I made things worse.  I backedup over all docs/files I wanted, along with firefox favorites, thunderbird and virtualbox VMs.  Installed 12.04, everything works...sort of.

I have crazy partitions!  Or, atleast I haven't seen anything like this.  

I have tried to use my virtualbox VMs that I copied over, and they aren't working.  In the past, I just opened up a VM directly from the folder, and it worked flawlessly. Now I am getting unrecognizeable issues, etc.  firefox works great and thunderbird imported ok too.

I guess the primary issue I want to resolve, is the partition item.  Is it better to just scrub the entire drive and start over?  What are these extra SWAP items?

secondly, any advice/thread to point me to on backup/restore VMs?

---

### Post by drs305 on 2012-07-21
Having an extra swap partition isn't a big problem. The best solution would probably be to keep only the sdb5 swap, since it is at the end of the partition. 

Use 'Partition, Swapoff' to unmount both swaps and then you should be able to delete the other one.

Next, go into /etc/fstab and ensure only a listing for sdb6's swap is listed. Remove any other swap listings.

---

