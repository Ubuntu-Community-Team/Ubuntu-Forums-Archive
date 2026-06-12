---
title: "Would ext4 install with ext3 /home partition cause problems?"
date: 2009-11-05
forum: General Help
---

### Post by Inane_Asylum on 2009-11-05
I recently installed Koala on an ext4 partition, but my /home partition is still formatted as ext3.  I've been having some random problems with 9.10 mostly involving internet connectivity, but with a few other problems (mounting, etc.) here and there.  Could this possibly be an issue, or is it just more run-of-the-mill Koala problems?

---

### Post by Giblet5 on 2009-11-05
I'm running four desktop and two laptop systems that way.

No problems at all, aside from some Just-Released dodginess.

---

### Post by Inane_Asylum on 2009-11-05
Thanks.  I guess I should've done a bit of research before jumping on a new upgrade :-/

Ah well, lesson well learned...

---

### Post by zcats on 2009-11-27
YES!  I have problems with this.  I did a fresh install of 9.10 choosing ext4 as / and leaving /home as ext3. All seems fine.....Then...
Sometime after an upgrade (kernel ureadahead, grub or other) this partition changed (WTF!!) to ext4 and the system would not boot cause could not mount /home (because fstab  had ext3 for the file system!). I did NOT mess with this partition trying to chnage it to ext4 or whatever...I tried mounting on the command line from live CD, but only mounting as ext4 would work. Once I changed the partition to ext4 in fstab and did e2fsck I could boot OK.  BUT I still have PROBLEMS:o
System totally  hangs and I have to do a power hard reset (opening another tty does not work) and then /home is corrupted again and cannot boot, fails fsck check on startup.  I have to manually boot live CD and do: e2fsck -f -v -y /dev/sdx
It finds problems (inode), corrects it and now boots OK.  This has happened twice so I really need to sort it out!
Perhaps I do not have "proper" ext4 on this partition (ie with attributes)?
How can I tell? What should I do to fix it?  :confused:

I was thinking of backing up home, re-formating partition to ext4 and then copying things back, but I am sure that there is an easier way that actually works out what is going on!
Any help would be appreciated:)

---

### Post by Pablisco on 2009-11-27
I think I'm having a similar problem. My computer just hangs... With the latest Linux kernel it doesn't even boot and with the one that came with 9.10 it just hangs at random times... The solution for me is to run it on Safe mode and it runs the file system checker.

This is very annoying since I am loosing coursework that I didn't have time to save. Anyone has a solution?

Thanks,

Pablo.

---

