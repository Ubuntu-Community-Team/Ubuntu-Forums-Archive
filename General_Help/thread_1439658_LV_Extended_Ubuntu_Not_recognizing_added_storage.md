---
title: "LV Extended Ubuntu Not recognizing added storage"
date: 2010-03-26
forum: General Help
---

### Post by josway on 2010-03-26
I have learned a little about LVM through tinkering but on my new setup I am having trouble. 

I am running Ubuntu 9.10 Server with Gnome desktop 64 bit.

I started with a 2TB HD and setup LVM with a LV for my data ("Storage) that mounts at /storage. That is full so I then added a second drive 500GB, formatted, added to VG and then extended the LV "Storage" with the 500GB partition. Now the LV reads as ~2.2TB which is right.  

Everything is successful up to this point. Except now when I go to the mounted LV at /storage Ubuntu shows it as full and only as ~1.7TB. The 500GB were never added! 

HELP!
Thanks.

---

### Post by srs5694 on 2010-03-26
It sounds like you extended the logical volume but not the filesystem it contains. You'll need to use whatever filesystem sizing tool your filesystem supports, such as resize2fs or resize_reiserfs, to get the filesystem to fill the logical volume. Be sure to read its man page before you do this. As a general rule, I recommend unmounting before you do this, even if the utility claims to allow resizing while mounted. (IIRC, the JFS resizer works during a mount operation, so you'll need to unmount and remount it to resize JFS.)

---

### Post by josway on 2010-03-26
Thank you! That did it.

You are a gentleman and a scholar. :D

---

