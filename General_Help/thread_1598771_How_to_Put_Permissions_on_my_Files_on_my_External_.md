---
title: "How to Put Permissions on my Files on my External Hard Drive"
date: 2010-10-16
forum: General Help
---

### Post by Sef on 2010-10-16
I have no permissions on my files on my external hard drive, and if I copy them over, I have no permissions on my home drive.

How do I put permissions on my files in the external hard drive, so they can be copied over to my home drive?

---

### Post by nothingspecial on 2010-10-17
I`m guessing the external drive doesn`t support linux file permissions. ntfs (maybe).

If so, you cannot put permissions on them.

---

### Post by matt_symes on 2010-10-17
Hi,

I think nothingspecial is correct. If you are only going to use it in *nux machines, format with ext3 or 4. If you plan to use it with windows as well  then you have to keep it as is.

Actually there are windows programs that allow you to access ext* volumes so you could format the drive as an ext* volume and have owners permission etc, however would you have to install these tools on _every_ windows box that needed to access the volume.

Kind regards

---

### Post by Rocket2DMn on 2010-10-17
You can mount manually using different mount options that will apply certain permissions to the entire mounted partition. These aren't "real" permissions, they are masks, but the OS will obey them. Specifically you would want to configure uid, gid, dmask, and fmask. After you copy them to your Linux formatted partition you can tweak properties there. In my home directory, most files are 644 and most directories are 755.

For example, dmask of 022 gives directories 755 permissions, and fmask of 122 gives files 644 permissions when mounted. Some more information about mount options can be found here - [https://help.ubuntu.com/community/Fstab#Options](https://help.ubuntu.com/community/Fstab#Options)
It also has a link to the mount man page.

---

### Post by oldfred on 2010-10-17
How are you copying? Some do not preserve ownership.

cp without -a and copying as sudo, root takes ownership (not good)

---

### Post by Sef on 2010-10-17
> oldfred: How are you copying? Some do not preserve ownership.

Originally I just dragged the files over, and then dragged the files back. I did partition it and reformat it as ext3 and ext4.


> Rocket2DMn: For example, dmask of 022 gives directories 755 permissions, and fmask of 122 gives files 644 permissions when mounted. Some more information about mount options can be found here - [https://help.ubuntu.com/community/Fstab#Options](https://help.ubuntu.com/community/Fstab#Options)
It also has a link to the mount man page.

Thanks for the link. I will have to check it out.

---

