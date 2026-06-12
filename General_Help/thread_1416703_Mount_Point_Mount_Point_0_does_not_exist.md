---
title: "Mount Point: Mount Point 0 does not exist"
date: 2010-02-26
forum: General Help
---

### Post by bill516 on 2010-02-26
I am dual-bootng Ubuntu 9.10 and Mint 8, both of which use GRUB2.  The Mint 8 GRUB sets the initial menu since Mint was loaded after Ubuuntu 9.10.  Since both use GRUB2 I was not concerned about this.

Both before the installation of Mint and afterward I see a series of messages fly by on the screen when Ubuntu is booted.  These come right after the initial presentation of the Ubuntu logo.

By restarting several times I can read the first several lines.  They are:

Mount:  Mount Point 0 does not exist
Mount 0 terminated with status 32
Mountall: Filesystem could not be mounted

Further lines follow but I would have to reboot umpteen times to have any chance of copying those.

I have looked in the various Ubuntu GRUB2 files for "Mount Point 0".  I do not see any reference to it.

GParted,  BKID and etc/fstab all agree on the UUIDs set for my Ubuntu/, Ubuntu Home and Ubuntu swap file.

I see nothing like this when I boot Mint 8.

My questions:

What is the point to error messages (I assume that is what they are) that fly by too quickly to be read?  Are they saved to a logfile somewhere?

What is "Mount Point 0"?

What does it mean in this context to say "Filesystem could not be mounted"?

This is all very curious because Ubuntu proceeds to mount and run just fine.

What is Ubuntu trying to do as it starts up that it cannot do?

How do I repair whatever has to be repaired in order to turn off these messages?

I have looked through such GRUB2 dcumentation as I can find without seeing any reference to this.  A Gogle search on "Mount Point 0" has not been helpful.

Mark me puzzled!

---

### Post by undecim on 2010-02-26
Sounds like a bad line in /etc/fstab. Can you open a terminal, type "cat /etc/fstab", and post the output here?

---

### Post by bill516 on 2010-02-26
Thanks undecim!  Here it is:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=bfde5bbd-019f-465a-85df-52753e573b4e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=dd20e5af-12c1-4fe6-b43a-7dc072446d9a /home           ext4    defaults        0       2
 sw              0       0
# swap was on /dev/sda6 during installation
UUID=774bd1da-9278-4c84-8792-3b5e8631f525 none            swap    sw              0       0


---

### Post by oldfred on 2010-02-26
I first thought this was a continuation that did not look right:

sw              0       0

I think you have an extra line.

---

### Post by Morbius1 on 2010-02-26
> UUID=dd20e5af-12c1-4fe6-b43a-7dc072446d9a /home           ext4    defaults        0       2
 [COLOR=Blue]sw              0       0[/COLOR]
# swap was on /dev/sda6 during installation
UUID=774bd1da-9278-4c84-8792-3b5e8631f525 none            swap    sw              0       0                      Appears to me that mount point 0 is the first 0 after "sw"

I'd make a copy of the current fstab and then just delete the "sw 0 0" line.

Open **Terminal**
Type **cp -a /etc/fstab /etc/fstab.bak**
Type [B]gksu gedit /etc/fstab

[/B][COLOR=RoyalBlue]EDIT: OOPS, Sorry. Simultaneous posts it seems.[/COLOR]

---

### Post by bill516 on 2010-02-26
My thanks to both morbius1 and oldfred!  I am running a data backup at the moment, so I won't fool with this until that is done.  Once done I'll edit as you suggest and report back.

I thought "sw 0 0" was a continuation of the prior line.  Notice it also appears at the end of the swap-file line.  I have no idea how it got to be where you see it.

I have to be admit that I do not understand even these simple lines well enough to spot a problem such as this.

So ASAP I'll do the edit, reboot and report back on how it works.

Once again my thanks!

---

### Post by bill516 on 2010-02-27
Apparently I did not post my final reply on this thread!  So to close the case, it turns out that both Morbius1 and oldfred were right, the devil was in that odd "sw 0  0" line in etc/fstab.  Ho did it get there?  Darned if I know but removing it restored a normal boot without all of the mount point verbage.

---

### Post by Yew Siong on 2011-03-16
I am having the same problem. This is what I get from fstab.


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults 0       0
# / was on /dev/sda1 during installation
UUID=bc0855ad-32f5-43c7-9e02-59d7cd33ebf2 /               ext4   
errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=92fdb2a3-ef09-46a3-aa91-7242f5b286df none            swap sw   0 0
F_drive /home/Host_F vboxsf defaults 0 0
D_drive /home/Host_D vboxsf defaults 0 0


anything wrong inside?:confused:

---

