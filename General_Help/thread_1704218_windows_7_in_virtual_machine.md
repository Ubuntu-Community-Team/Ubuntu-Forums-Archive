---
title: "windows 7 in virtual machine"
date: 2011-03-10
forum: General Help
---

### Post by rahulbest on 2011-03-10
i have ubuntu on my pc......i downloaded virtual machine...now i want to install windows 7 32bit on it...how much memory should i allocate for it???
and can i delete that windows 7 after some days???and that memory can i use in ubuntu??

---

### Post by uRock on 2011-03-10
I think that Windows 7 needs at least 1GB of RAM. That RAM will only be used when you have the VirtualBox running, so when you shut the VM down the RAM will be available to the rest of the machine again.

---

### Post by howefield on 2011-03-10
> **rahulbest said:**
> can i delete that windows 7 after some days???and that memory can i use in ubuntu??

Just to add, the VM hard disk that you will create to install Windows 7 is simply a file that resides on top of the host file system, and can be deleted at any time, or backed up to another disk/partition if you wanted.

---

### Post by rahulbest on 2011-03-10
i mean to say u have to allocate hard disk space for it...so how much i have to allocate???

---

### Post by uRock on 2011-03-10
> **rahulbest said:**
> i mean to say u have to allocate hard disk space for it...so how much i have to allocate???

I would say at least 10GB for W7.

---

### Post by needlpt on 2011-03-10
If you are using Virtual box, make it a dynamically expanding disk, sized at 16GB or more.  That's what I did, and it only grew to 9.1GB (so far).

Windows on a dynamic disk tends to grow, but not shrink.

---

### Post by Mark Phelps on 2011-03-10
Unless you're only going to install the basic OS, with no apps and no updates, 20GB would be better -- as it will give you some space to install stuff.  And be advised, SP1 has been pushed out and that takes space by itself.

---

### Post by howefield on 2011-03-10
For Windows 7 Microsoft recommends 16 gig minimum for 32 bit and 20 gig minimum for 64 bit with a further 15 gig needed if you plan on using XP mode.

Don't sell yourself short on disk space as it is easier to have too much than not enough.

---

