---
title: "Seperate partition both for /home and Windows personal documents?"
date: 2010-03-12
forum: General Help
---

### Post by Pott on 2010-03-12
I dual boot Ubuntu and Vista. I don't have a whole lot of personal files (mostly everything is on the external HDD) and so I have a spare 55GB partition sitting around with nothing on it, and an almost full Vista 60GB partition.

Is it possible to use this spare partition both as a /home and as a Windows Documents partition..? 

I'd need to set Ubuntu to automount it and it'd need to be in FAT32 or NTFS for Windows to recognize it but I don't see why it shouldn't work... even though I have no clue how :s 

I'll keep on researching but I couldn't find much concrete info on the topic. I'll try different search terms meanwhile.

Thanks!

---

### Post by Ilalmi on 2010-03-12
Hi,

it is possible. If you format the partition with ext2 or ext3, you can access it from Windows using Ext2 IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)).
I'm using it and it works great.

---

### Post by Pott on 2010-03-12
Great thanks :)

My Linux partition is formatted in Ext4. It'd mean having the /home directory formatted in Ext3 however using this driver. Would that cause any issues?

---

### Post by philinux on 2010-03-12
Why not have a data partition formatted to ntfs. Both system can then read/write to it

/home needs an ext type system that supports permissions.

---

### Post by Pott on 2010-03-12
So wait... I'd need to seperate the Documents, Download, Pictures, Music etc... from the /home partition..? Not quite sure how I'd get on with doing this...

---

### Post by srs5694 on 2010-03-12
Personally I'd use FAT, or NTFS if I needed to store large files, and either mount it under my user directory in Linux (/home/{username}/Documents, say) or mount it elsewhere and set up a symbolic link (/home/{username}/Documents -> /mnt/shared, for instance). That way, Linux would still be able to store its user configuration files and so on in a Linux-native filesystem that Windows wouldn't touch, but user access to the shared directory would still be quite easy. Using ext2 or ext3 might work with the Windows driver, but I haven't been following it closely, so I don't know how reliable it is. Using this driver might give Windows access to other Linux partitions, which is something that I personally would prefer not doing. (Of course, using another Linux filesystem, such as ReiserFS or XFS, for other Linux partitions would work around this problem.)

Mounting a partition somewhere specific can be done by editing /etc/fstab, as in:

```

/dev/sda7        /mnt/shared    ntfs    uid=1000,dmask=000,fmask=111       0 0

```

This mounts /dev/sda7 at /mnt/shared, assigning ownership to UID 1000 and setting the default permissions such that anybody can access the partition, if I got it right (I haven't tested this specific example, and the options are from memory).

I believe there's a way in Windows to mount filesystems in a more Unix-like way, so you could do something similar in Windows. I don't know the Windows configuration settings to do this, though. Try Googling the topic.

---

### Post by srs5694 on 2010-03-12
> **Pott said:**
> So wait... I'd need to seperate the Documents, Download, Pictures, Music etc... from the /home partition..? Not quite sure how I'd get on with doing this...

The usual directory structure for home directories is:

```

/home
   -> ./user1
       -> Documents
       -> Download
       -> {more user files}
   -> ./user2
   -> ./{more users}

```Replace "user1" and "user2" with the names of the directories assigned to specific users. In theory, you could mount a shared directory anywhere -- at /home, at /home/user1, at /home/user1/Documents, etc. In practice, you'll run into problems if you mount a FAT or NTFS partition at /home, since Linux expects to be able to use ownership and permissions on that directory's subdirectories, and neither FAT nor NTFS supports this, at least not in a way that Linux can use. I'm not sure if you could do it as the user level, either (/home/user1, /home/user2, etc.); I've never tried it. The safest way is to either mount the shared directory at a subdirectory of a specific user's directory or mount it somewhere else entirely and create a symbolic link. Note that the subdirectories created for you in your home directory (Documents, Download, etc.) are just conventions. You can use them or ignore them as you see fit, although you may need to reconfigure some programs to not use them. If necessary, you could create symbolic links from multiple locations into the same place, or a subdirectory of one place. For instance, mount your shared partition at /mnt/shared, create Document, Download, and other subdirectories in it, and then link your Documents directory to /mnt/shared/Documents, your Download directory to /mnt/shared/Download, etc. (You'll need to delete or rename your current Documents, Download, etc. directories to create the symbolic link using the ln command.)

---

### Post by Pott on 2010-03-12
Ah I think I see. So I'd need to create a sub directory called Documents where to move all my Documents, Downloads, Images etc... and then put this into another partition in NTFS, which Linux then accesses through symbolic links?

---

### Post by srs5694 on 2010-03-12
> **Pott said:**
> Ah I think I see. So I'd need to create a sub directory called Documents where to move all my Documents, Downloads, Images etc... and then put this into another partition in NTFS, which Linux then accesses through symbolic links?

You do this:


[list=1]
[*]Create an NTFS or FAT filesystem on your shared-documents partition.
[*]Create an /etc/fstab file entry for your shared-documents partition, as specified earlier.
[*]Mount your FAT or NTFS shared-documents partition. Typing "mount -a" should do this, once the /etc/fstab entry is in place.
[*]Copy your /home/{username}/Documents, etc. directories to /mnt/shared. Typing "cp -r ~/Documents /mnt/shared" will do this for your Documents directory. (Or you can use a GUI file manager. If you use text mode, be careful with your trailing slashes ("/"), lest you copy a directory's contents rather than the whole directory.) Repeat for any others you want to share. If you get permissions errors, investigate; you may need to adjust your /etc/fstab entry and re-mount.
[*]Rename your ~/Documents and other directories.
[*]Create symbolic links. Typing "ln -s /mnt/shared/Documents ~/" will do this for Documents. Repeat as necessary for other directories.
[*]Once you're satisfied everything is working, the files are accessible and aren't corrupted, etc., delete the original directories that you renamed two steps ago.
[/list]

---

### Post by Pott on 2010-03-12
That's a good starting point, thanks! I'll do some research on this. I don't quite know what symbolic links are but it should be easy to figure this out.

---

### Post by srs5694 on 2010-03-12
Symbolic links are special files that contain pointers to another file or directory. When you access the symbolic link, the result is just as if you accessed the linked-to file, at least for most purposes. Symbolic links are used "behind the scenes" for a lot of things in Linux, and as in this example, they can be handy for ordinary users, too. Windows has its equivalent, but I've forgotten what name is used ("shortcut," maybe?).

---

