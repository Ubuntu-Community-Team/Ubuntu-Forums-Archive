---
title: "Merging 2 physical drives into one?"
date: 2009-08-13
forum: General Help
---

### Post by nbx909 on 2009-08-13
Here's what I have. I have Ubuntu 9.04 installed on /dev/sda (sda1 mount point is / and sda5 is swap) and I have a windows partition on /dev/sdb. What I want to do is wipe windows off and merge the new partition into /. After a google search I determined a way to do this is LVM. My question is do I have to use LVM or is there an alternative? If I do use LVM do I have reinstall ubuntu to do so or can I install and use LVM with out reinstalling? The main reason is because I am going to use this server for backups so really I just need the extra space for one folder is it possible to expand one folder across two partitions?

Thank you in advance,

---

### Post by michy99 on 2009-08-13
Use that folder as the mountpoint for the second drive.

---

### Post by nbx909 on 2009-08-13
I'd like the extra 50gb from the current ubuntu drive added

---

### Post by michy99 on 2009-08-13
> **nbx909 said:**
> I'd like the extra 50gb from the current ubuntu drive added

Well, that changes things. I'm not sure how you would do that.

---

### Post by Bachstelze on 2009-08-13
LVM is the only way I know. And yes, you will have to reinstall Ubuntu.

---

### Post by capscrew on 2009-08-13
> **nbx909 said:**
> Here's what I have. I have Ubuntu 9.04 installed on /dev/sda (sda1 mount point is / and sda5 is swap) and I have a windows partition on /dev/sdb. What I want to do is wipe windows off and merge the new partition into /. 

I agree with the other posters if what you want to do is use 2 physical drives as one logical volume (partition).  But you do not have to do this to accomplish your goal.  

You seem to mix the two terms in your description.  Drives are not the same as partitions.

I personally do not like creating volumes (two drives that appear as one partition).  There are alternatives to this. > 

After a google search I determined a way to do this is LVM. My question is do I have to use LVM or is there an alternative? If I do use LVM do I have reinstall ubuntu to do so or can I install and use LVM with out reinstalling? 
If you do not want to re-install you can mount the old Windows partition to a new mount point somewhere in the original file system.  As an example I have a 500GB partition mounted to the original file system at /backup.> 
The main reason is because I am going to use this server for backups so really I just need the extra space for one folder is it possible to expand one folder across two partitions?

In addition you can have multiple partitions on a drive (sdb1 and sdb2 in your case) if you wanted.  Each partition can have it's own mount point, for example: /dev/sdb1 @ /backup and /dev/sdb2 @ /archive.> 

Thank you in advance,

---

