---
title: "HD I/O errors - non-working installation"
date: 2009-08-04
forum: General Help
---

### Post by Nerevar144 on 2009-08-04
I am trying to get a working ubuntu studio.  I am dual booting with windows 7 on a 1 TB drive.  I have tried 8.04 LTS and 9.04 versions formating in ext2,3 and 4.  

My problem is that no matter what I do I get HD I/O errors either during boot up which prevent boot up during the ubuntu studio loading screen, or after successfully booting the system will either lock or not allow me to launch any programs citing I/O errors:confused:.  Sometimes ubuntu can't even load the icons of the applications.  

I've notice using windows disk management the partition sizes are reported as differently in the ubuntu installer.  A discrepancy of about 6GB (windows says about 78GB and ubuntu says 84GB for the ubuntu partition).  I've tried making the partition 78 GB during the ubuntu installation thinking that for some reason the ubuntu installer was trying to format more than was actually there.  Right now i'm burning a standard 9.04 desktop edition ubuntu installer and am going to see if that fixes it.  Any ideas?

---

### Post by Nerevar144 on 2009-08-04
I just noticed that during the installation of ubuntu desktop 9.04 sda2, 3, and 4 are missing and ubuntu offers to install to sda 5 for the ext3 partition and sda6 for swap.  I looked in gparted and sda 2, 3, and 4 are there yet I am unable to do anything to them... ubuntu tells me that they are busy although they are completely unaccessible.  I am currently installing the 9.04 as we speak.  Lets see if this install has the same problems.

---

### Post by Nerevar144 on 2009-08-04
Well seems the problem is actually the real time kernel.  Anyone know how to configure it so it will work for me without the HDD I/O errors?

---

