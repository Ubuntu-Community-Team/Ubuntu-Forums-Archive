---
title: "File permissions"
date: 2012-04-29
forum: General Help
---

### Post by HappyHappyJoy on 2012-04-29
This is a basic question, I apologize for that, but I can't seem to find the answer on google.  Long story short, I had a linux installation on my main hard drive and I had an encrypted second hard drive for secure data storage.  My main hard drive crashed.  I am not terribly concerned about that, as everything I wanted on that was backed up using Ubuntu1.  However, some of the data on the second hard drive was not backed up. I am using a livecd now, and when I try to access my second, encrypted hard drive it tells me that I don't have the proper file permissions.   Is there any way to get around this, or should I just view this as a costly lesson?

Thanks in advance.

---

### Post by kurja on 2012-04-29
> **HappyHappyJoy said:**
> This is a basic question, I apologize for that, but I can't seem to find the answer on google.  Long story short, I had a linux installation on my main hard drive and I had an encrypted second hard drive for secure data storage.  My main hard drive crashed.  I am not terribly concerned about that, as everything I wanted on that was backed up using Ubuntu1.  However, some of the data on the second hard drive was not backed up. I am using a livecd now, and when I try to access my second, encrypted hard drive it tells me that I don't have the proper file permissions.   Is there any way to get around this, or should I just view this as a costly lesson?

Thanks in advance.

try if you can get to your files with ```
gksudo nautilus
```

---

### Post by forbidden404 on 2012-04-29
I know other way to get permission in a hard drive;

```

$ sudo apt-get install ntfs-config
# ntfs-config

```
Now you select the HD and put as read/write.

---

### Post by kurja on 2012-04-30
isn't that just for ntfs partitions?

---

### Post by forbidden404 on 2012-05-03
> **kurja said:**
> isn't that just for ntfs partitions?

For the other types nautilus didnt work?

---

