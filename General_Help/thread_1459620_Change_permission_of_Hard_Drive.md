---
title: "Change permission of Hard Drive?"
date: 2010-04-21
forum: General Help
---

### Post by TurtleKing on 2010-04-21
I am getting annoyed that every time I try to extract, move, or delete a folder I get: 
"Unable to move due to file permission"
"Unable to delete due to file permission"
"Unable to extract due to file permission"
I really have a hard time trying to use, and understand the chmod folder stuff in terminal. So I asked a friend and he helped me create a desktop program or icon where I would just drop the folder I wanted to use on it, and permission wouldn't be needed anymore.

Well, I dropped a a folder on it one day and the folder didn't open, so I tried another folder and eventually the thing never worked again so I removed it.

*Is it possible to allow the entire hard drive or OS (Ubuntu 9.10) to give me permission to all the folders?* I only installed the [**password to log**] in thing, so I wouldn't have to worry about people in my house using my computer without consent. If this isn't possible can someone post a method to create the launcher or icon?

Note: I made a root desktop thing (Guy holding what looks to be an ID card) but not even that will allow me to delete the folder in the file system. I the entire game that the folder is called is removed already, so there is no point me leaving this folder alone.

---

### Post by Jguy on 2010-04-21
If you need to do stuff in folders and files in a grahpical interface (move around or extract to directories such as /usr and /etc then you can open a terminal and type 'gksudo nautilus', and that will open a file browser with root permissions, allowing you unrestricted access to your machine in a graphical interface. Be absolutely careful with what you delete while doing this. You could potentially damage your system.

You should be able to, even if your /home was mounted on a different partition, have full access to your home directory. If you have another drive that you need full access to (and you have it mount in the same place everytime), then chmod maybe the best and safest way.

You cannot chmod or change the permissions to yourself for the entire system, (well you can, but it won't start back up)

---

### Post by oldfred on 2010-04-21
You need to understand the linux way of permissions and mounting of partitions.
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

If you have a basic understanding you can permanently mount with this, but you really need to have some understanding of what settings to use:

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

---

### Post by ajgreeny on 2010-04-21
If it is your one single disk on which your OS is installed then you will not be able to change the permissions globally, or if you do you will not be able to boot.

If you are asking about a second hard disk used for storage or something similar, you can certainly make that disk do whatever you want by changing the mode and ownership of its mount point folder.

However, it would be good to know more about what you're trying to do before passing on any more details as there may be simpler and safer ways to do what you want.

---

