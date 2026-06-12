---
title: "Migrating /home partition to a new drive"
date: 2009-11-02
forum: General Help
---

### Post by daetsy on 2009-11-02
I'm wanting to move my /home partition to a larger hard drive without losing all my settings, but I don't have a clue how to go about it. I'd appreciate any pointers. Thanks.

---

### Post by P4man on 2009-11-02
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by cariboo on 2009-11-02
Just move your complete user directory to the new drive, them mount it in the home directory. I would suggest using the Live CD to make the move easier.

Next depending on the partition label I would mount it like this:

```
sudo mount /dev/sdb1 /home
```

where /dev/sdb1 is the partition or disk where moved your home directory to.

You can then edit /etc/fstab to mount the directory automatically the line in /etc/fstab should look something like this:

```
/dev/sdb1   /home           ext4    defaults        0       2
```

You will have to substitute your device label for the one in the example.

---

### Post by daetsy on 2009-11-03
How do I move the /home directory. I made a new install of 9.10 on the new drive and created a /home partition then copy/pasted it into the new /home, but everything was padlocked and I couldn't take ownership.

Would I be better cloning the whole drive? If so, is there an app (preferably with GUI) in the repos?

Also can you tell me why there are so many spaces in the second line of code, and are they important?

---

