---
title: "can fat32 partition be used as /usr or /home"
date: 2010-08-22
forum: General Help
---

### Post by rockager on 2010-08-22
can a fat32 partition be marked as /usr or /home during or after installing ubuntu?

---

### Post by Morrad on 2010-08-22
> **rockager said:**
> can a fat32 partition be marked as /usr or /home during or after installing ubuntu?

I know that the /home partition absolutely can.  It's one of the ways that I've heard some people share documents between Windows and Linux if they dual boot.

As far as I know, doing this does screw up the file permissions, however.

---

### Post by anirudhtomer on 2010-08-22
See if you mount it on /usr. Your machine will give you a prompt with a message
"Missing *****(I forgot this message...I tried to do this a few months ago) " 

All of your programs which are run from the /usr directory will stop working.
Since you need root privileges for unmount & sudo resides on /usr you won't be able to unmount that as well. The only way left is to login via other virtual consoles as root & unmount that.

as far as mounting on /home is concerned you can do that and even access files on that /home folder but don't expect your wallpaper & other files to stay there coz /home files are replaced by those FAT32 files

---

### Post by oldfred on 2010-08-22
NO.

Windows formats do not support linux file permissions and ownership. Part of why Linux is more secure by design of the system.

You can not use FAT or NTFS for /home but can mount another NTFS partition for shared data which I recommend if you are dual booting with windows. I recommend NTFS as it is better than FAT but some devices like 4GB or less flash cards may require it for compatibility with your camera or other device.

---

### Post by anirudhtomer on 2010-08-22
ya you can mount it on /home & read the files but I tried to open it in write mode with sudo for which it gave permission denied.

---

### Post by bodhi.zazen on 2010-08-22
> **oldfred said:**
> NO.

Windows formats do not support linux file permissions and ownership. Part of why Linux is more secure by design of the system.

You can not use FAT or NTFS for /home but can mount another NTFS partition for shared data which I recommend if you are dual booting with windows. I recommend NTFS as it is better than FAT but some devices like 4GB or less flash cards may require it for compatibility with your camera or other device.

This is the correct answer ^^

Although Linux can rw to both fat and ntfs partitions, neither ntfs nor fat support linux permissions, and many config files need specific permissions.

You could probably make it work , but probably without a desktop, I am not sure on that.

---

