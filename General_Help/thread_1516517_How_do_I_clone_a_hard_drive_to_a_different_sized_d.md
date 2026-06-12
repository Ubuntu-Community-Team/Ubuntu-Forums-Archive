---
title: "How do I clone a hard drive to a different sized drive?"
date: 2010-06-23
forum: General Help
---

### Post by josephellengar on 2010-06-23
I am soon going to have to return my intel ssd for replacement.  Therefore, I am going to be cloning the 160gb drive to a 320gb drive to keep my system settings while I am waiting for my new drive.  I will not change the size of the partitions to fill the 320gb drive.  I'll just change the grub settings if I absolutely have to.  After that, I am going to have to clone the 320gb drive back to the replacement 160gb drive.  Am I going to have problems doing that since I will be going from a larger to a smaller drive?  I typically use Clonezilla with the default settings.

---

### Post by dcstar on 2010-06-24
> **rossholley said:**
> I am soon going to have to return my intel ssd for replacement.  Therefore, I am going to be cloning the 160gb drive to a 320gb drive to keep my system settings while I am waiting for my new drive.  I will not change the size of the partitions to fill the 320gb drive.  I'll just change the grub settings if I absolutely have to.  After that, I am going to have to clone the 320gb drive back to the replacement 160gb drive.  Am I going to have problems doing that since I will be going from a larger to a smaller drive?  I typically use Clonezilla with the default settings.

If you are returning to the same size drive then just use dd for both operations, it keeps things simple.

---

### Post by Mark Phelps on 2010-06-24
> **rossholley said:**
> ...Am I going to have problems doing that since I will be going from a larger to a smaller drive?  I typically use Clonezilla with the default settings.
If you don't resize during the first cloning operation, you should have no trouble going back.  Clonezilla will not let you clone to a smaller drive.

---

