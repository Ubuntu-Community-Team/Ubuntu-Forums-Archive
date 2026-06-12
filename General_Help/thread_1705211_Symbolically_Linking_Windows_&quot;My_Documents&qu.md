---
title: "Symbolically Linking Windows &quot;My Documents&quot; With Ubuntu's Home on Dual Boot System"
date: 2011-03-11
forum: General Help
---

### Post by moon2js on 2011-03-11
Hi all,

I'm refurbing an old laptop for someone who's not technically savvy. Just about any Linux/GNU OS works better on this (maybe decade old) hardware than the Windows XP it comes with. That said, I'm going to reformat and set it up to dual boot with XP and Ubuntu, so that the user has the option to use Windows if needed.

I'm planning on using symbolic links between the user's home directory on the Ubuntu partition and My Documents on the NTFS side. I think I remember using something called NTFS-config in the past to automount the Windows partition on Ubuntu. If someone knows a better way, please let me know.

Next, I'll link the Documents and Settings/User folders on the NTFS partition to a freshly installed Maverick partition like this:

```
cd ~
rmdir Documents
ln -s /media/Windoze/Documents\ and\ Settings/User/My\ Documents/ Documents
rmdir Desktop
ln -s /media/Windoze/Documents\ and\ Settings/User/Desktop/ Desktop
rmdir Music
ln -s /media/Windoze/Documents\ and\ Settings/User/My\ Documents/My\ Music/iTunes/iTunes\ Media/ Music
rmdir Pictures
ln -s /media/Windoze/Documents\ and\ Settings/User/My\ Documents/My\ Pictures/ Pictures
rmdir Videos
ln -s /media/Windoze/Documents\ and\ Settings/User/My\ Documents/My\ Videos/ Videos
rmdir Downloads
ln -s /media/Windoze/Documents\ and\ Settings/User/My\ Documents/Downloads/ Downloads
```

This way, I hope that Windows and Ubuntu applications can share files (music, videos, documents, etc) and I can make the Ubuntu partition a lot smaller because a lot of those user files will be stored on the NTFS partition. This will obviously only work for one user only, and if the user saves a document in /home/user/, it won't be easily visible on the Windows side.

Can anyone spot any issues with this config and/or recommend better methods?

---

### Post by Krytarik on 2011-03-11
Your chosen setup is generally fine.

But you can simply use "fstab" to automount the Windows partition, like this (of course you have to choose the right UID/GID or just remove those options, I don't know anymore if they are really necessary):```

UUID /media/Windoze ntfs-3g rw,nosuid,nodev,allow_other,default_permissions,umask=007,uid=1000,gid=46 0 0
```To get the UUID, run those command:
```
sudo blkid
```[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

And you could also use "fstab" to bind the respective directories, instead of symlinking them, like this:
```
/media/Windoze/Documents\ and\ Settings/User/My\ Documents /home/USER/Documents bind
```Also, you may need to symlink certain files/dirs of the user profiles of Firefox and/or Thunderbird if the user uses those.

---

### Post by dcstar on 2011-03-12
> **moon2js said:**
> 
..........
This way, I hope that Windows and Ubuntu applications can share files (music, videos, documents, etc) and I can make the Ubuntu partition a lot smaller because a lot of those user files will be stored on the NTFS partition. This will obviously only work for one user only, and if the user saves a document in /home/user/, it won't be easily visible on the Windows side.

Can anyone spot any issues with this config and/or recommend better methods?

NTFS is **not** a Linux filesystem, it does not support many Linux attributes and it certainly does not support OS operations that Linux systems assume will be available to it in a system controlled folder like /home.

Just use an app - like Gedit - that uses the Linux hidden file designator (the leading ".") on an NTFS filesystem and see what happens. Many Linux apps use hidden files/folders that will crash when used on NTFS and there will be other issues with other incompatibilities.

Some apps may work but there are no guarantees, and it is just basically silly to mix unsupported filesystems.

---

### Post by Krytarik on 2011-03-12
That's why I would leave it by symlinking only those directories the OP has mentioned.

---

