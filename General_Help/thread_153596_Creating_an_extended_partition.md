---
title: "Creating an extended partition"
date: 2006-04-01
forum: General Help
---

### Post by Master Shake on 2006-04-01
Here's the deal..  I need to create an extended partition so I can install another distro.  I already have 4 primary partitions, and 6 GB of unallocated space.  The unallocated is what I want to install the other distro on.  How would I best go about this?  What tool would be best suited for the job?  Gparted?  QTParted?  Some command line util?

---

### Post by taurus on 2006-04-01
You need to convert one of your primary partitions to extended partition.  Then, you can create as many logical partitions as you want under that extended partition...

---

### Post by Master Shake on 2006-04-01
Okay, but how do I do that?

---

### Post by Ramses de Norre on 2006-04-01
sudo apt-get install gparted
gksudo gparted &
Delete one of the existing primary partitions (after having it backed up), As you want to use the unallocated space, choose the partition before or behind the unallocated space.
Select the whole new unallocated space and make it into an extended partition.
Then you'll need to make two (or more) logical partitions inside the extended one (don't know what exactely to click on but it will be one op the options when you right click on the extended partition).

---

### Post by Master Shake on 2006-04-01
Hmmm...  I'll have to give that a shot.  I was hoping for an easier way...

Welp, there ya go.  Thanx!

---

