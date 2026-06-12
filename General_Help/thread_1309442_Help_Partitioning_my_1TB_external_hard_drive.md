---
title: "Help Partitioning my 1TB external hard drive"
date: 2009-11-01
forum: General Help
---

### Post by kehon on 2009-11-01
I bought a 1TB hard drive to store and backup all of my files recently and I'm needing a little help partitioning it. 
Here is the current layout:

930GB Total
**_--type (label) size_**
--ntfs (ntfs) 30GB
--ext3 (ext3) 30GB
--truecrypt (encrypted) 100GB
--lvm2 (ufiles) * (rest of space avail.)
{
  --ext3 (ufiles) 300GB
  --none (unallocated) * (rest of space I haven't used)
}

the problem is I would like to be able to easily mount the lvm on most linux distros and maybe also have a way to mount it on windows if possible or at least read only. Right now I'm working on linux and I'm on ubuntu 9.10. It shows the encrypted lvm that the system is running on as a drive and when I plug in the external drive it shows the lvm also. But it needs root privileges to mount the lvm2. Is there another partioning scheme that I can do to achieve what I want since I plan on having many more partitions in the remaining space such as music, documents, etc...(I think)?

Hard drives only support 4 partitions that's why I choose lvm2.

---

### Post by blueridgedog on 2009-11-01
Just for my own clarification....you are using lvm as a type of extended partition in order to have a larger number of partitions on the drive?  In order to suggest a alternative, share more about why you selected LVM versus an extended partition.

---

### Post by kehon on 2009-11-01
the lvm2 is an primary partition and I choose lvm instead of extended partions because I though it would be about the same but it could also hold more partitions and it had volume groups and associated names so it would look neater.

---

### Post by blueridgedog on 2009-11-01
LVM has a lot of utility in aggregating volumes, but it is limited in that it is not supported by other operating systems.  I would recommend an extended partition.  In reality, you only need three partitions.  One ntfs, one ext3 and your truecrypt one.  You could use your fourth for an extended, keeping your options open for the future.

---

### Post by kehon on 2009-11-01
thank you. I was unaware of how the extended partition works. I looked it up and found that it's very much like an lvm and gets the same job done for me and is also cross platform for the most part.

---

### Post by kehon on 2009-11-01
one more thing. I have ubuntu installed on an encrypted lvm and I was wondering if I could encrypt an extended partition instead and run ubuntu from it

---

### Post by blueridgedog on 2009-11-02
It should work the same way, but I am no expert on encrypted partitions.

---

