---
title: "Unusual icon next to icon..."
date: 2006-05-07
forum: General Help
---

### Post by morbid_bean on 2006-05-07
I copied something off of my flash drive to my desktop and there is a little pad lock next to it.....WTF?

---

### Post by Sutekh on 2006-05-07
What filesystem format is your flash drive?

---

### Post by morbid_bean on 2006-05-07
i belive its fat32 or ntfs

---

### Post by Sutekh on 2006-05-07
Ok.  Have you done anything to get the flash drive working with Ubuntu?  Or do you just plug it in and it comes up on your screen/desktop?

---

### Post by morbid_bean on 2006-05-07
I just plug it in and go about my buisness.

---

### Post by Sutekh on 2006-05-07
Roger.  Problem is Ubuntu doesn't really seem to know what to do when devices with Windows formatting are plugged in.  It lets you access the device, but not in a way that you can do what you want.  

FAT/NTFS partitions are mounted by default as being owned by the 'root' user, not your user, and probably with restricted permissions.  Its just the way Ubuntu deals with Windows partitions by default.

You can confirm this by right-clicking that file with the padlock and choosing Properties -> Permissions.  Is the owner 'root', what permissions (read, write execute) have been enabled?


You can pretty much do two things.  Change the way in which Ubuntu handles your flash drive, so that your user owns the file and there are no restrictions on permissions.  The only problem is I think you will lose that plug-and-play effect.  

You should use this link to change the way Ubuntu handles FAT/NTFS formatted partitions

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

 - I'd be happy to explain this further


The other option is to keep that default mounting situation, and then just change the permissions of the files once they are copied across.

You can always change the properties of files on your Desktop.  If you wish to change the owner of the files to your user, this is the command you need.
```
sudo chown **user:user** <name of file>
```
 - this command should be run from the folder containing the file
 - **user** is your username

Then to change the permissions of the file so that you have full access use this command
```
sudo chmod 777 <name of file>
```
 - the number 777 allows read/write and execute permission.

---

### Post by morbid_bean on 2006-05-07
Ok thanks for the help. :)

---

### Post by Sutekh on 2006-05-07
No problem.  :)

Sing out if you need more help.

---

