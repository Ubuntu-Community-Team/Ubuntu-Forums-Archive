---
title: "Disk check on every boot on lucid"
date: 2010-05-26
forum: General Help
---

### Post by goniomdq on 2010-05-26
Hi everybody,

I have updated from Karmic to Lucid not long ago, and everything went smooth and my system is been working like a charm for about a month. And it still does, with the only issue being that every time I restart my system, one of my partitions is checked.
My disk is split into 4 partitions:
sda1, NTFS for windows
sda2, ext4 for "/"
sda3, ext2 for /home
sda4, swap

Now what seems to happen is that sda3 is being marked as "not clean" on every shutdown, which makes me assume that is not being umounted at all.

I've been reading logs, commenting network drives out on fstab.. nothing does the trick.

I've booted into single mode and run e2fsck (which doesn't find anything wrong, and marks the FS as "clean") and then rebooted. The result is: if the FS wasn't mounted when I restart, then I get a clean boot once, but it is checked on the following one; if it was mounted then it is again checked at start-up.

Again, all points to the problem being that the FS is not cleanly umounted on shut-down.

Does anybody have a clue?
I could not find any log with info of the processes killed and FS umounted at shut-down, so if anybody knows where to look, it could be a good start.

Thanks a lot.

---

### Post by dino99 on 2010-05-26
clean the system:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

will force a fsck on next boot:

sudo shutdown -F -r now

---

### Post by goniomdq on 2010-05-26
Nup..
The system was clean, as the apt and dpkg commands did nothing.
And then reboot, let the e2fsck go through and next reboot a new disk check.

Thanks anyway!
Any other ideas?

---

### Post by goniomdq on 2010-05-27
Anybody?

---

### Post by interzoneuk on 2010-09-27
Hi

You can force an fsck on next boot by using

sudo touch /forcefsck

the reboot.

You could add the line

touch /forcefsck

to

/etc/rc.local  (above exit  line) to get this to occur all the time.

Cheers

---

