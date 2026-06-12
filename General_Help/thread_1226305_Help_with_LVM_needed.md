---
title: "Help with LVM needed"
date: 2009-07-29
forum: General Help
---

### Post by uge on 2009-07-29
Hi,

I need help with LVM.

So I installed Ubuntu 8.04 TLS using the alternate install disk.

I chose the option that's called something like "use whole disk and set-up LVM"

The installation proceded fine.

BUT I have a second drive, that I'd like to use !

In the GNOME GUI I can't see it anywhere.

During the install, I used the "manual" option while in the partitions setup to created a logical LVM partition on the second drive.

I don't know if it worked, and I don't think it is even formatted. I don't know how basically.

oh, BTW, if you haven't figured out, I'm a newbie in the linux world :S

...and maybe there's a LVM configuration I need to change somewhere too ??


Basically, what I wanna do is consider those two 1 TB drives as a 2 TB partition and eventually add more drives if needed, while still having to deal with just one partition.


Please help !!

---

### Post by Johnius on 2009-07-29
I had the same trouble, don't worry.  If you really want to use LVM, you need to format both disks in the install as logical partitions, create a logical group (in the LVM manager, which appears after logical partitions are designated), create a logical volume (the next step in the LVM), then set your other partitions within the partition manager with the logical volume you created.  I wish I had screenshots for you.

But, if you just want to have 2tb from two 1tb disks, you may want to consider a hardware RAID, it might be easier.  Stripe the two disks together, and Linux should recognize it as one disk.

---

### Post by uge on 2009-07-29
Hey thanks for the reply !

Thought of RAID but didn't use it because
1) I once lost everything with RAID so I'm a little traumatised.
2) If I want to add a third drive in the future, I won't be able to do so.

Now my question is : do I really need to reinstall everything ?

I mean : I already got the first drive set up for LVM.

Can't I just format the second drive in LVM, and mess with the LVM configuration and everything is cool ?

I mean, isn't that the whole point of LVM ? You set it up right when you install Linux, then you can just add more drives when needed ?


THANKS !

---

### Post by Johnius on 2009-10-25
I forgot to subscribe to this thread.  My apologies.  Yes, that is the point of LVM, to just add drives when you need them.  If you have your first drive set up as LVM, you should just be able to use the LVM utilities (e.g. vg add, etc.) to add the drives.  I hope you found what you were looking for!

---

