---
title: "Ubuntu 904 CPU stuck"
date: 2009-07-28
forum: General Help
---

### Post by map7 on 2009-07-28
I'm running Ubuntu 9.04 on an AMD-FX53 with 2GB RAM and an SSD running off a SATA PCI controller card.  The motherboard is an ASUS A8V Deluxe.

The computer keeps freezing up and on the terminal it keeps printing error messages like:
**BUG: soft lockup - CPU#0 stuck for 61s! [console-kit-dae:2486]**

I'm able to recreate this problem very fast by running bonnie++ and it fails within a few minutes.

I've read other peoples posts on this BUG and followed their advice with no luck.  This advice included:
Run a memory test - I ran memtest86 for 20hours with no errors.
Disable ACPI - I've added acpi=off and noacpi to my kernel boot line in grub, this didn't stop the problem.

I've also ran a CPU test to see if it was overheating using 'burnK7' for 3hours.  The CPU reached 65C but didn't freeze.

It only seems to freeze when there is a lot of disk activity.  I've changed hard drives but get the same problem.

Both HD's were SSD's.  The SSD's I'm using are OCZ Core Series 2 which I run in another computer with out a problem.  I actually moved the SSD which was failing this the AMD-FX53 computer to my other computer and it hasn't had a problem for two weeks, even after running bonnie++ for a few hours.

I'm lost as to what else to try.

I've recently upgraded another computer to Linux Mint 7 and it has the exact same problem.

---

### Post by map7 on 2009-08-20
I've installed a second copy of Ubuntu 904 64bit on the same hardware and hard drive this time using an ext3 format instead of ext4.

I first ran my tests again on the ext4 to prove that it still fails, which it did in 20 minutes.

I then ran the same tests on the ext3 system and it ran fine.  

The same thing happens with the other computer.  So it looks like EXT4 has some issues still.

---

### Post by CHaoSlayeR on 2009-10-19
Could you try to update the BIOS on your machines?

I had similar issues and that fixed it for me.

C]-[aoZ

---

