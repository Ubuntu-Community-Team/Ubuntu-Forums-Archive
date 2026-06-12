---
title: "USB Flash drive: cannot copy data into"
date: 2009-07-25
forum: General Help
---

### Post by indranama on 2009-07-25
last week, I got 3 USB flash drives from my friends, which I couldn't write any file INTO those drives. Ubuntu makes an error message that these drives are Write Protected. I tried in Windows, it worked normally.

I can copy files FROM the drive, only I cannot write INTO them.

Is there a way to solve this problem?

---

### Post by kjohri on 2009-07-25
You can check the permissions. The flash drive would be mounted in a directory, say /media. Give the commands,

cd /media
ls -ls

See whether the user-id with which you have logged in has the permission write on the disk, say /media/disk.

Also, you can see the files on the flash disk.

cd /media/disk
ls -lsa

This should give an idea about the files on the flash disk, permissions and the space taken up by existing files.

---

### Post by indranama on 2009-07-25
> **kjohri said:**
> 
This should give an idea about the files on the flash disk, permissions and the space taken up by existing files.

Hello, thanks for reply,
then can I set permissions to the files of disk, to grant privileges to write into it?

---

### Post by kjohri on 2009-07-25
Yes, you do that. Hopefully, data on the USB flash disk is not critical. You may lose the data, in case something goes wrong while giving the commands. If it is critical, take a backup. Or do the experiment with some other flash drive with non-critical data.

---

