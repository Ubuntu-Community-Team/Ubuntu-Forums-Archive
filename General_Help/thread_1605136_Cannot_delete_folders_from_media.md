---
title: "Cannot delete folders from /media"
date: 2010-10-24
forum: General Help
---

### Post by mwa_023 on 2010-10-24
I am trying to delete some folders from my /media folder, however, I the folders, and the files in them are undeleteable.


They are from a failed install of america's army. instead of installing to one of my partitions, it created a new folder, with the name of the partition in /media. it is >800mb of stuff I'd LOVE to delete.

and since AA used its own installer, (I did not use the software center) I cannot simply uninstall via it.

:confused:

thank you!

---

### Post by rhoparkour on 2010-10-24
The folder /media actually shouldn't contain anything that is externally mounted on your computer i.e. a cd or an external hard drive. That's why it won't let you delete anything.

If you're sure this isnt from a cd or something that you left in the tray or on a usb port this should work. MIND YOU, I DON'T KNOW WHAT THIS WILL DO IF THIS IS NOT FROM A FAILED INSTALL, ATTEMPT AT YOUR OWN RISK.

---- Deleted bad advice ----

BEFORE YOU DO ANYTHING, PLEASE MAKE SURE THE FOLDER IS NOT A MOUNTED CD OR EXTERNAL DRIVE, THE NEXT STEPS WILL CLEAR THE PARTITION IN WHICH AA TRIED TO INSTALL

EDIT: I don't think this was a completely failed install, if you're saying it should've installed in a separate partition, it did. 

The folder /media does contain mounted partitions that are not Ubuntu's (let's call them external partitions).

So what you're seeing is  the AA partition mounted on your computer. If you want to clear it of everything just go to 

System > Administration > Disk Utility

You should navigate to where you can see your hard drive partitions, form here you can unmount the desired partition and Format if you so wish.

---

### Post by yetiman64 on 2010-10-24
> **mwa_023 said:**
> I am trying to delete some folders from my /media folder, however, I the folders, and the files in them are undeleteable.


They are from a failed install of america's army. instead of installing to one of my partitions, it created a new folder, with the name of the partition in /media. it is >800mb of stuff I'd LOVE to delete.

and since AA used its own installer, (I did not use the software center) I cannot simply uninstall via it.

:confused:

thank you!

Before attempting to rm anything. Did you install from a cd? They are mounted in media.
Can you post back the output of
```
ls -l /media
``` and indicate which contents are the ones in question.

800 MB is about the size of a cd.

Edit: and don't format any partitions at this stage please.

---

### Post by mwa_023 on 2010-10-24
thank you for the replies.

I am positive that the folder I want to delete is not a mounted drive.

it shares the same name of a partition on my computer, however

here is the output requested:
> 
mwa@mwa-desktop:~$ ls -l /media
total 24
lrwxrwxrwx 1 root root    7 2010-10-06 14:05 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-10-06 14:05 floppy0
drwxr-xr-x 3 root root 4096 2010-10-17 16:23 hd ubuntu aux
drwx------ 4 mwa  mwa  4096 2010-10-14 22:24 HD Ubuntu Aux
drwx------ 1 mwa  mwa  8192 2010-10-17 19:56 HD XP Aux
drwx------ 1 mwa  mwa  4096 2010-10-18 19:50 HD XP Mainalso see this screenshot: [http://mattanastasio.com/shot1.png](http://mattanastasio.com/shot1.png)
thanks again all!

---

### Post by yetiman64 on 2010-10-24
> **mwa_023 said:**
> thank you for the replies.

I am positive that the folder I want to delete is not a mounted drive.

it shares the same name of a partition on my computer, however

here is the output requested:
also see this screenshot: [http://mattanastasio.com/shot1.png](http://mattanastasio.com/shot1.png)
thanks again all!

**Partitions in your machine are mounted in /media**. Games you install are installed to a folder within a partition. **To format a whole partition to clear out one folder is potentially disastrous for your setup**. I advise caution as to what steps you take.

Did the installer indicate where it was installing to? (not just the partition, but the actual location)

If not have a look in /usr/games for a folder relating to the game, or even in your home folder (show hidden files as well in your home folder).

Best to locate it before nuking the partition it was installed to :).

---

### Post by mwa_023 on 2010-10-24
aye, I'd rather not nuke anything that would cause an issue!

however I am still quite confused with why I am having this problem- but allow me to clarify the circumstances that caused it.

I have 2 HDs. HD1 is 20gb slpit between xp, ubuntu, and a swap.

HD2 is 320gb split into two partitions- "hd XP Aux" and "hd ubuntu aux"

whilst installing america's army, it asked for a location to install it to. wanting to install my programs on to the larger partiton (HD Ubuntu Aux) I typed in /media/hd ubuntu aux

I thought this would install it to that location. (I do not think the drive was "mounted" at the time of install)

So, as i believe was illustrated in the screen shot I linked previously, the HD Ubuntu Aux (note the case of the letters) seems to be my drive partition according to Ubuntu and according to its icon.

hd ubuntu aux (all lowercase) is the folder where AA is installed. AA does not run. there is nothing from AA under /usr/games. like wise I cannot delete anything from within this folder.


I'm not crazy am I?

---

### Post by yetiman64 on 2010-10-25
> **mwa_023 said:**
> aye, I'd rather not nuke anything that would cause an issue!

however I am still quite confused with why I am having this problem- but allow me to clarify the circumstances that caused it.

I have 2 HDs. HD1 is 20gb slpit between xp, ubuntu, and a swap.

HD2 is 320gb split into two partitions- "hd XP Aux" and "hd ubuntu aux"

whilst installing america's army, it asked for a location to install it to. wanting to install my programs on to the larger partiton (HD Ubuntu Aux) I typed in /media/hd ubuntu aux

I thought this would install it to that location. (I do not think the drive was "mounted" at the time of install)

So, as i believe was illustrated in the screen shot I linked previously, the HD Ubuntu Aux (note the case of the letters) seems to be my drive partition according to Ubuntu and according to its icon.

hd ubuntu aux (all lowercase) is the folder where AA is installed. AA does not run. there is nothing from AA under /usr/games. like wise I cannot delete anything from within this folder.


[COLOR=Blue]I'm not crazy am I[/COLOR]?

[COLOR=Blue]A: No[/COLOR] :). It can all get confusing with naming of folders and mounting of drives etc ;), even for the more experienced.

Just to be absolutely safe, run in terminal and post the output of,
```
cat /etc/fstab
```this is just a precaution for me to check drive mounting locations.

Then could you post back the output of 
```
ls -l /media/"hd ubuntu aux"
```I would actually like to see the AA folder before issuing an rm command.

Your last post has clarified the situation nicely and sounds like the installer has made a new folder in /media (as instructed to, but because of the drive mounting done to here can cause critical confusion).

---

### Post by mwa_023 on 2010-10-25
```
mwa@mwa-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=cce62c34-d19e-45e2-80e2-23c24405d775 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
mwa@mwa-desktop:~$
```and

```
mwa@mwa-desktop:~$ ls -l /media/"hd ubuntu aux"
total 4
drwxr-xr-x 15 root root 4096 2010-10-17 17:11 armyops
mwa@mwa-desktop:~$
```
So it looks like mounted drives are case sensitive?
Does having\not a drive mounted at time of install mean anything?..on that note...what exactly does it mean to mount a drive? Sounds like more than just making a shortcut on the desktop.... :\

Thanks again!

---

### Post by yetiman64 on 2010-10-25
> **mwa_023 said:**
> 
```
mwa@mwa-desktop:~$ ls -l /media/"hd ubuntu aux"
total 4
drwxr-xr-x 15 root root 4096 2010-10-17 17:11 armyops
mwa@mwa-desktop:~$
```So it looks like mounted drives are case sensitive?
Does having\not a drive mounted at time of install mean anything?..on that note...what exactly does it mean to mount a drive? Sounds like more than just making a shortcut on the desktop.... :\

Thanks again!
That is the contents I needed to see. 

Yes the mounted drives like any path in Linux are case sensitive (just change case of 1 character and it becomes different to what you want :), can be a pain at times)

You will note I asked you about /etc/fstab (fstab= filesystem table), nothing in there to bother about by the way, this file is used to automatically mount filesystems (read that as partitions as well) at startup. This is where an entry would have been written at install time if you had of included them (can be put at any time though- it really doesn't matter).
Here is a link FYI about [[COLOR=Blue]--fstab--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=283131"), a very good and in depth guide to fstab.

The main difference with mounting compared to a shortcut is the contents are actually loaded to the mount postition whereas a shortcut is only a pointer to another location as far as I understand it.

Now before I forget ;), the command you need to remove the failed install is
```
sudo rm -r /media/"hd ubuntu aux"
```Notes for your info,
1. **sudo** raises the following commands' privileges to that of root (needed as you are working outside your home directory, which is all owned by root)
2. **rm** is the remove command. Always be **extremely cautious** about using this **especially** with root privileges, it can be very destructive if the wrong path is accidentally inputted.
3. **-r** is the recursive swith, which tells rm that a folder and all its contents are to be deleted (the command won't work without it).
4. **/media/"hd ubuntu aux"** is the exact location you need to remove.

Please also check in your home directory for any hidden folders related to AA (programs can hold config files in your home directory sometimes.)

**Edit:** just realized, you should check in /media/hd ubuntu aux/armyops for an uninstall file first. If one is there let us know as it would be better to try use it first.

Cheers from yetiman64.

---

### Post by Mike Green9 on 2013-01-17
Thanks yetiman64 for this:


sudo rm -r /media/"hd ubuntu aux"
I have been trying for a week to get rid of a folder erroneously opened in /media to no avail. Thanks to you it  is gone :D.

I guess I missed the "-r" switch. That did the trick.

Have a good day,

M...

---

