---
title: "Can't change permissions for anything"
date: 2010-10-13
forum: General Help
---

### Post by Fallen_Enigma on 2010-10-13
When I go into Properties > Permissions, if I click on anything, such as a check box, or a dropdown box, it will check (or open), then revert back to it's original settings. My user has the permissions for the file/folder, but it won't change. Is there any way to fix this?

---

### Post by efflandt on 2010-10-13
What permissions are you trying to change and is it in your home directory or somewhere else?  If it is on a mounted system, that system (or mount point) might be read only (or if flash memory like SD, maybe the switch on it is in the Lock position).  If it is a FAT32 file system, that knows nothing about file permissions and has no way to set them.  So if you cp a file from FAT32 to a Linux system, it would appear to have read, write, and execute permission for anybody.

If the files or directory is not owned by you, I would normally use **sudo chmod** from a terminal.  But you have to know what you are doing to not accidentally make something inaccessible.  See **man chmod** in a terminal.

For example a directory needs **x** permission in order to do a directory listing and **r** permission in order to read files.  So for a directory **sudo chmod a+rx** or **sudo chmod 755** would give anyone permission to list or read files.

If you want to give everyone read permission for a file it would be **chmod a+r** or **chmod 644**.  Or for anyone to execute a script it would be **chmod a+rx** or **chmod 755**.  This assumes you use **sudo** in front of the command if not owned by you.

---

### Post by WorMzy on 2010-10-13
> **efflandt said:**
> If it is a FAT32 file system, that knows nothing about file permissions and has no way to set them.

Same for NTFS.

---

### Post by Fallen_Enigma on 2010-10-13
I have my system partitioned to run Ubuntu (10.10) and Windows 7. I'm trying to change the permissions of my W7 files, and that's where the problem is.

EDIT: I'm trying to make a file executable as a program.

---

### Post by WorMzy on 2010-10-14
You can't change the permissions on them. At least, not like that. You have to set the owners and the permissions for the entire partition at mount time by setting the uid, gid and umask in fstab.

e.g.
```
/dev/sda1 /media/windows ntfs auto,**uid=1000**,**gid=1000**,utf8,**umask=002** 0 0
```

However, if you're doing what I think you're doing, then you just need to open a terminal and run
```
wine <path/to/executable.exe>
``` instead of double-clicking the executable.

---

### Post by Fallen_Enigma on 2010-10-16
Ok, so I have looked at fstab in gedit, but I didn't see anything where I could change the uid, gid, and umask. I also don't have an sda1 folder as well.

When I tried the second option, it couldn't open the program still.

Also, I'm sorry for the delayed reply. School kept me busy.

---

### Post by WorMzy on 2010-10-16
/dev/sda1 is just a device file for the first partition on the first hard drive, it's not actually a folder. What that line would do is mount that partition onto /media/windows with the declared options.

If your windows partition isn't sda1, then you can find out what it is by running

```
sudo fdisk -l | grep NTFS
```

Alter the fstab line I posted to suit your needs. So if your Windows partition is sdb3, add this line to the bottom of fstab:

```
/dev/sdb3 [COLOR="Red"]/media/windows[/COLOR] ntfs [COLOR="Red"]auto,[/COLOR]uid=1000,gid=1000,utf8,umask=002 0 0
```

If you want the partition to be mounted somewhere other than /media/windows, then change the mount location to where you want it to be mounted. If you don't want the partition to be automatically mounted when you boot up, then remove the "auto" from the list of options. You will need to create the folder that you want to mount the partition to though, otherwise you'll get an "No such directory" error when it tries to mount it.

```
sudo mkdir [COLOR="Red"]/media/windows[/COLOR]
```

Read the [fstab man page]("http://manpages.ubuntu.com/manpages/maverick/en/man5/fstab.5.html") for more information about how to use fstab.


Did wine give you a reason why it couldn't run the program? You could try copying the file to your home directory, and executing it from there; since your home directory is on a linux filesystem, you can change the permissions on files as you see fit.

---

