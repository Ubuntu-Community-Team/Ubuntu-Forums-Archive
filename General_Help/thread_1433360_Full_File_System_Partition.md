---
title: "Full File System Partition"
date: 2010-03-18
forum: General Help
---

### Post by codeblue2k on 2010-03-18
I installed Ubuntu on an 80gb hard drive that I had laying around. Is is a media server so it just sits in the closet. Well today I went to log into it and it says the File System partition is completely full and im not sure why. Here is what I see when I run gparted:
```

/dev/sdb1  ext4       Size: 71.66GiB  Used: 69.38GiB  Flags: boot
/dev/sdb2  extended   Size: 2.86GiB
    /dev/sdb5 linux-swap   Size: 2.86GiB (This is a partition in sdb2)
```

Are my partitions not right?

---

### Post by codeblue2k on 2010-03-19
I dont know if it makes a difference or not, but I forgot to mention that I have been transferring over 500Gib of files around my network. 

So to clarify, I have an 80Gib drive with a base Ubuntu Desktop install. I have only installed Samba and a dive mounting application that I cant remember the name of. Other then that the machine sits in my closet and hosts out files. Last week I made a large backup of all the files I have on the server (about 500GiB), to a little NAS i have on my network thru a mount point and rsync. All a sudden my drive is completely full and im not sure why. 

Any thoughts?

---

### Post by ubunterooster on 2010-03-19
with nautilus, browse the filesystem and see how much space each folder is taking up

---

