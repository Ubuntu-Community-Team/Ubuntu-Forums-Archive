---
title: "dashing bar of death during partition shrinkage?"
date: 2011-09-11
forum: General Help
---

### Post by princeofnam on 2011-09-11
I decided to shrink my extended ext4 partition down from about 350 to 122 GB.  Then I plan to format the free space to a NTFS logical partition.  Thing is during the resize step in gparted I haven't had progress for the past 30 minutes.   The progress bar doesn't pop up and instead the dashing bar going left and right has been showing the entire time.  Usually gparted doesn't take this long for me.  Anyone have any ideas?

I want to cancel and possibly see if it'll shrink any better if I split the two actions but hitting cancel I'm promted with a warning that I may cause "severe damage" if I do so.

---

### Post by ottosykora on 2011-09-11
I have so far not used this on ext4, but had much longer times on some ntfs drives and even some ext3 drives.

So try to observe it for other hour or so.

---

### Post by ajgreeny on 2011-09-11
> **princeofnam said:**
> I decided to shrink my extended ext4 partition down from about 350 to 122 GB.  Then I plan to format the free space to a NTFS logical partition.  Thing is during the resize step in gparted I haven't had progress for the past 30 minutes.   The progress bar doesn't pop up and instead the dashing bar going left and right has been showing the entire time.  Usually gparted doesn't take this long for me.  Anyone have any ideas?

I want to cancel and possibly see if it'll shrink any better if I split the two actions but hitting cancel I'm promted with a warning that I may cause "severe damage" if I do so.
Are you sure it is still resizing the extended partition?  That would normally be quick as the extended partition is just a wrapper for several logical partitions.  Also once you have shrunk the extended partition, which is not ext4 by the way, but may contain several possibly ext4 partitions, you will not be able to make another extended partition containing a NTFS logical partition.

So, I think you have got your terminology confused, or you are trying to do something which can not possibly be carried out, hence the problem, perhaps.

Which is it, do you think?

---

### Post by ottosykora on 2011-09-12
oh yes, and one thing more: if someone tries to make some operation on ntfs partitions, it should not be done together with other operations at the same time, just this operation alone.

---

### Post by Mark Phelps on 2011-09-12
My experience using GParted has been very different from yours.  

Everything takes a very L...O...N...G time -- sometime, HOURS, to complete.  GParted does the work twice, once to check for errors, and then a second time, for real. 

So, seeing no progress for 30 minutes, is (in my experience) nothing unusual at all.

---

