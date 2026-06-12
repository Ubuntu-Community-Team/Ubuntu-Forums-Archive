---
title: "I can't using partition  after install ubuntu."
date: 2011-10-23
forum: General Help
---

### Post by nguyenabcd on 2011-10-23
I install ubunttu with type "alongside win7". Then I boot from CD, but I can using partition feature in normal. I mean I want to go into file manager

---

### Post by oldtimer7777 on 2011-10-24
> **nguyenabcd said:**
> I install ubunttu with type "alongside win7". Then I boot from CD, but I can using partition feature in normal. I mean I want to go into file manager

I don't really understand what you are asking, but I will take a stab in the dark. 

Don't boot from CD after you install Ubuntu.

Boot Ubuntu from your hard drive that you installed it on.

Login.

Then open file manager. 

Let us know if that solves it.

---

### Post by nguyenabcd on 2011-10-24
Thank!
I want to reinstall win 7. There are my plan:
Format win7 in dev1 = dirive C???.
Resintall win 7.

Is it correct. 
How I can format a dev???

---

### Post by Mark Phelps on 2011-10-24
If you have a Win7 installation DVD (not CD), you can try booting from it and seeing if it gives you the option of reformatting the entire drive.

If that option is not there, you need to boot from an Ubuntu desktop CD, use the Try Ubuntu option, then use Disk Utility to deleten the Linux filesystem partitions on the drive. Then, try rebooting with the Win7 installation DVD, select the free space, and let the Win7 installer do the formatting.

---

### Post by nguyenabcd on 2011-10-24
I have only Win7 CD. I will try.

---

### Post by Mark Phelps on 2011-10-24
> **nguyenabcd said:**
> I have only Win7 CD. I will try.

Win7 does not come on a CD; it only comes on a DVD.

So, if what you have is REALLY a CD, not DVD, and your PC came with Win7 preloaded, then it is most likely an OEM-provided Restore CD.  When you boot from this, it's likely the only thing you will be able to do is "restore" your PC to it's original state when it had Win7 on it.

Also, unless you made a set of recovery CDs, which you would have mentioned, if this is a Restore CD, it will need to use a saved compressed Win7 image hidden somewhere on your hard drive, most probably, a Recovery partition.  If you erased or otherwise damaged that partition installing Ubuntu, you will not be able to restore Win7 using that CD.

---

