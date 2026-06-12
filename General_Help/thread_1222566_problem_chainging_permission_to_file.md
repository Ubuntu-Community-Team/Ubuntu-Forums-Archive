---
title: "problem chainging permission to file"
date: 2009-07-25
forum: General Help
---

### Post by Mia_tech on 2009-07-25
guys, I have a partition on my main drive that I use for storage of docs, which I created under root, and I mount under /media/storage but now I'm trying to give another user rwx permision with
```

sudo chmod -R o+rwx /media/storage
```

but when I go back and do ```
ls -l /media/storage
``` is still reflecting the old permissions; therefore, not giving write access to the other user.... what am I missing here?

thanks

---

### Post by wojox on 2009-07-25
I think you have to add the user name and group.

---

### Post by Mia_tech on 2009-07-25
> **wojox said:**
> I think you have to add the user name and group.

I just read the ```
man chmod
``` file and didn't mention anything about using the uid or guid, which would make sence why use ```
o+rwx
``` or ```
a+rwx
``` if you don't want to give all user rwx and just give it to a single user.... there's probably a way; I just haven't found it yet

thanks

---

### Post by aesis05401 on 2009-07-25
Hello, 

You could create a group, add only yourself and the other user to this group, then 'chown' the mountpoint to your group.

Then anyone else who wants access to the data can just be added to the group that has access to that data.  Either way, the /media/storage mountpoint needs to be created in a way that permits you to give someone else access.

Check out the 'mount' man page for more info.  There are options like --bind/--rbind to mirror mountpoints for other users, and ways to do read-only mirrors with shared subtree mounts etc.. 

Anyhow, the definition of the mount could be messing you up.

---

### Post by michy99 on 2009-07-25
What filesystem is the drive? If it is fat32 or ntfs, the permissions are established when the drive is mounted.

---

### Post by Mia_tech on 2009-07-26
is a local partition, I originally created it in fat32, but is giving me so many problem with permission that I changed it to ext3, ant the permission worked just fine

---

### Post by aesis05401 on 2009-07-26
> **Mia_tech said:**
> is a local partition, I originally created it in fat32, but is giving me so many problem with permission that I changed it to ext3, ant the permission worked just fine

Where are you creating the mount point and can you post the commands?

Is this an fstab entry?  Is the other user local or accessing this share from across the network?  If local, have you added 'users' to the fstab entry?

---

### Post by Mia_tech on 2009-07-26
> **aesis05401 said:**
> Where are you creating the mount point and can you post the commands?

Is this an fstab entry?  Is the other user local or accessing this share from across the network?  If local, have you added 'users' to the fstab entry?

yes, I got it working

---

