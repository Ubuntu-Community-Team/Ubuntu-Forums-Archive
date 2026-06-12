---
title: "Permission script"
date: 2006-05-04
forum: General Help
---

### Post by Calle on 2006-05-04
Hi!

I've recently been copying lots of files from an NTFS-partition to a ext3 partition. The problem is that all of the files copied from the NTFS-partition have the permissions dr-xr-xr-x which is not really good because I can't write to my own files without setting the +w permission parameter first. But it isn't really tempting to do that on every file and folder on the new partition. 

Is there any script or something like that, looping through child folders from a given folder and set permissions from input? I *do* have the opportunity to make the whole copy session once again, so if there is something I could do before that to prevent uncool file permissions, I'd be glad to hear.

Thanks in advance!

---

### Post by frodon on 2006-05-04
First, the command umask allow you to set the rights that a new file will have after its creation, so you can choose the mask you want. i advice you to put the umask command in your .bashrc file.
For example the command "umask 002" will set 775 rights by default for each new created file.

The command to change the rights on a file is chmod and the -R option allow you to do it for a whole directory including its sub-directories, so you can change all the rights with one command.

Give me more details about how you want to change the rights and i will try to help you if you get problems.

---

### Post by Calle on 2006-05-04
Thanks frodon. I wish to enable all permissions for owner, read and execute for group and read for others. If I set umask 002 in my .bashrc, will that have an effect on the mounted files when I mount my NTFS partition to /media/ntfsdisc?

---

### Post by frodon on 2006-05-04
First you have to know that FAT32 and NTFS file systems don't support unix rights therefore it's not possible to change the rights on these file systems. The only way using file systems to set some rights is through the mount commant and on the whole partition.
links:
[http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS](http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS))
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Anyway for your ext3 partition this command will do the job for the directory you want including all its sub-directories : ```
sudo chmod -R 764 *the_directory_path*
```

The umask option has an effect only for the files you will create and only with file systems which support unix rights

---

### Post by dschulz on 2006-05-04
This will do in a clever way,

# Fix files perms
sudo find /path -type f -not -perm 644 -exec chmod -v 644 {} \;

# Fix directories perms
sudo find /path -type d -not -perm 755 -exec chmod -v 755 {} \;

# Set the desired owner for the files/dirs in the path
sudo find /path -not -user theowner -exec chown -v theowner:theowner {} \;

---

### Post by Calle on 2006-05-05
Thanks, both.

---

