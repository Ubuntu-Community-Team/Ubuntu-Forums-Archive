---
title: "extra Lost+Found folder (NOT the one in / directory)"
date: 2012-07-24
forum: General Help
---

### Post by jatwood on 2012-07-24
I've done a search here and on google and can't seem to find the answer.

Background:

I have a separate partition that is mounted in /home via the fstab under a custom folder name. We'll call it the "store" folder, and it automounts during every startup. Now I use this folder for storage only. I don't have any programs or scripts run from this folder. It's owned by me of course, the user.

Problem:

Every time I delete or move a file from within this directory a Lost+Found folder is created. I find this extremely annoying as I already have one under /. I'm not looking to "hide" it because that's not solving my problem. Furthermore, the .Trash-1000 folder appears too when something is deleted or moved. I don't need these folders. They already exist under the user name's home folder.

When I do remove both the Lost+Found folder and .Trash-1000 folder from /home/store they reappear after doing what I described above.

What can I do to permanently stop these folders from being "auto-created"? (for lack of a better term)


Just for clarification
So the directory looks like this:

/home

store/
john/

(while inside /home)

$ ls -lsha

4.0K drwxr-xr-x 20 user  user  4.0K 2012-07-24 07:14 store
4.0K drwxr-xr-x 41 user  user  4.0K 2012-07-24 12:00 john

---

### Post by redmk2 on 2012-07-24
> **jatwood said:**
> I've done a search here and on google and can't seem to find the answer.

Background:

I have a separate partition that is mounted in /home via the fstab under a custom folder name. We'll call it the "store" folder, and it automounts during every startup. Now I use this folder for storage only. I don't have any programs or scripts run from this folder. It's owned by me of course, the user.

Problem:

Every time I delete or move a file from within this directory a Lost+Found folder is created. I find this extremely annoying as I already have one under /. I'm not looking to "hide" it because that's not solving my problem. Furthermore, the .Trash-1000 folder appears too when something is deleted or moved. I don't need these folders. They already exist under the user name's home folder.

When I do remove both the Lost+Found folder and .Trash-1000 folder from /home/store they reappear after doing what I described above.

What can I do to permanently stop these folders from being "auto-created"? (for lack of a better term)


Just for clarification
So the directory looks like this:

/home

store/
john/

(while inside /home)

$ ls -lsha

4.0K drwxr-xr-x 20 user  user  4.0K 2012-07-24 07:14 store
4.0K drwxr-xr-x 41 user  user  4.0K 2012-07-24 12:00 john

There is a lost+found directory in the root of any partition.  It's part of the file recovery system.  It will be recreated if you delete it.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://serverfault.com/questions/6753/what-happens-if-i-delete-lostfound").

The .Trash-1000 folder is also at the root of a partition.  It is created by Nautilus.  This will also be recreated if you Nautilus.

---

### Post by CatKiller on 2012-07-24
> **jatwood said:**
> I don't need these folders. They already exist under the user name's home folder.

Not true. The folders you're thinking of are on a different partition. Copying data to a different partition when you delete something would be stupidly pointless; what actually happens is that the location pointer gets changed to indicate that the file is considered to be in the Trash. Nice and cheap and quick, and almost nothing needs to be written.

Just stick Lost+Found in a text file at the base of that partition called .hidden and forget about it. And don't send things on that partition to the Trash.

---

### Post by jatwood on 2012-07-24
> **redmk2]
There is a lost+found directory in the root of any partition.
[/QUOTE]

What about USB thumb drives or external HD? I don't see lost+found  folders on them. The same should apply to a separate partition. Also, I  don't see how there is a "root" directory under this partition or any  other like an external HD or USB. It's a device and should be mounted as  such.


[QUOTE=CatKiller said:**
> ...hidden and forget about it. And don't send things on that partition to the Trash.

That's an awkward workaround don't you think? So I can't delete anything on that partition unless I use a bash command like rm.

My guess is that this has something to do with fstab or nautilus.

---

### Post by CatKiller on 2012-07-24
> **jatwood said:**
> What about USB thumb drives or external HD? I don't see lost+found  folders on them. The same should apply to a separate partition. 

I don't think removable drives get fsck'd, and so a lost+found directory would never be used, AIUI, but I could be wrong. And I guess one would have to be created if you ran a manual fsck on a removable drive.

You definitely get .Trash directories on removable drives if you send something to the Trash from them, though.

> Also, I  don't see how there is a "root" directory under this partition or any  other like an external HD or USB. It's a device and should be mounted as  such.
That's because you aren't thinking about it. A partition gets mounted to a mount point. That directory is the root directory of the mounted partition. If you mounted that partition somewhere else, the files you'd created in that root directory would appear at the new mount point.

Your main partition is mounted at /, which is why / is often called *the* root directory, although then people get confused with /root, which is the *user root*'s Home directory.

Your idea of "mounting a partition as a device" would be doing file operations on /dev/sda2, which would be stupid. Partitions are mounted into the filesystem hierarchy to serve a particular purpose.

> 
That's an awkward workaround don't you think? So I can't delete anything on that partition unless I use a bash command like rm.

My guess is that this has something to do with fstab or nautilus.No, you can delete things. You just can't send them to Trash, since that will cause a Trash folder to be created to hold them (obviously).

It's Nautilus that creates the Trash folder when you implicitly tell it to. I'm not sure what creates the Lost+Found directory.

Hide them, forget about them and stop fiddling with them is my advice, but you know that already.

---

### Post by redmk2 on 2012-07-24
> **jatwood said:**
> What about USB thumb drives or external HD? I don't see lost+found  folders on them. The same should apply to a separate partition. Also, I  don't see how there is a "root" directory under this partition or any  other like an external HD or USB. It's a device and should be mounted as  such.
The lost+found directory is a consequence of *fsck*.  It is recreated every time the *fsck* command is run.  Although there is both a fsck.vfat and a fsck.ntfs I can't tell you they make a lost+found directory.  The command fsck for EXT2/3/4 certainly does. 

It's the 'root of the partition" on a "root" directory.  Yes there is a .Trash-1000 folder created when you use Nautilus on any partition.  Here is file listing of one of my USB sticks mounted at /media/STICK```
/media/STICK$ ls -la
total 9
drwx------ 1 red red 4096 2012-07-24 12:32 .
drwxr-xr-x 4 root  root  4096 2012-07-24 12:32 ..
-rwxrwxrwx 1 red red   19 2012-07-11 09:57 test.doc
-rwxrwxrwx 1 red red    0 2012-07-24 12:32 testing
drwx------ 1 red red    0 2012-07-11 09:44 .Trash-1000

```
...As you can see the .Trash-1000 directory is hidden. 
> 
That's an awkward workaround don't you think? So I can't delete anything on that partition unless I use a bash command like rm.
Speaking for myself, it's not a workaround at all.  You can delete the files with Nautilus.> 
My guess is that this has something to do with fstab or nautilus.
Nothing to do with fstab.  Nautilus creates the .Trash directory.  I have a script that I run that cleans out the .Trash files on the various partition I have.


[COLOR="Blue"]Edit: Now you have the same answer twice[/COLOR] ;-)

---

### Post by jatwood on 2012-07-24
> **CatKiller said:**
> ...
Your idea of "mounting a partition as a device" would be doing file  operations on /dev/sda2, which would be stupid. 

Could you elaborate on that? Calling it stupid doesn't really help or give a deeper explanation.

> **CatKiller said:**
> ...Partitions are mounted  into the filesystem hierarchy to serve a particular purpose...

In this case, I simply store my files here instead of the user's /home folder. The main logic behind this is that I have a bunch of directories in my storage folder and I don't want them to be in the same directory as the /home/user folder. There are already a bunch of extraneous folders that ubuntu puts in the /home/user directory such Pictures, Documents, etc.--I don't want any intermixing of those directories. That's why I've chosen to put my files on a separate partition.

I also don't want to simply "hide" this folder or the trash folder. I indicated this in my original post.

> **CatKiller said:**
> ...No, you can delete things. You just can't send them to Trash...

That's the same thing. Yes, I know that the trash serves as a temporary place for deleted files. Who goes around deleting files without nautilus or a window manager though? I want to delete my files or move them, or do whatever I want without all these extra folders being created. I don't think that's unreasonable or impossible thing to ask for in a partition. If it were a partition that were mounted at / then I could understand because / has it's own Lost+Found in it, but my storage partition is not mounted at that level. It's mounted under the home folder.

---

### Post by CatKiller on 2012-07-24
> **jatwood said:**
> Could you elaborate on that? Calling it stupid doesn't really help or give a deeper explanation.

Imagine if Windows had only drive letters, and every time you used a different machine (and occasionally on a re-boot) the letters were different. Like that.

> I also don't want to simply "hide" this folder or the trash folder. I indicated this in my original post.Yes, you did. It doesn't stop it being the sensible option. If fsck never finds any corrupted data and you don't move anything to the Trash, they'll never have anything in so why does it matter if they're there but hidden? (This is a rhetorical question; I don't actually care why you care)

> That's the same thing.No, it really isn't.

---

### Post by CatKiller on 2012-07-24
> **jatwood said:**
> In this case, I simply store my files here instead of the user's /home folder. The main logic behind this is that I have a bunch of directories in my storage folder and I don't want them to be in the same directory as the /home/user folder. There are already a bunch of extraneous folders that ubuntu puts in the /home/user directory such Pictures, Documents, etc.--I don't want any intermixing of those directories. That's why I've chosen to put my files on a separate partition.

I also don't want to simply "hide" this folder or the trash folder. I indicated this in my original post.

I have thought of another solution, although it does have it's limitations so you might not like it.

So far we have:

[LIST]
[*]Simply hiding the directories that you don't want to see, which is quick & easy.
[*]Allowing the directories that you don't want to see to be created and automatically deleting them. redmk2 has said that he does this. A crude method would be something like a cron job to delete them (if they exist) at specified times. A more elegant method would be to use something like DBus notifications to only delete them when they are created, rather than running a script that does nothing most of the time. If you're going to nuke your Trash file from orbit anyway, though, you might as well just delete things rather than moving them to Trash in the first place. IMO.
[*]The new idea I had, which is to mount your partition somewhere else (/mnt/something would be the usual place) and then symlink the directories in that partition to directories in your Home folder. The advantages are that you don't need to see or otherwise fiddle with the directories that bother you so much, whilst still having them exist for the Trash folder and fsck functionality. The disadvantage is that you'd need to make new symlinks whenever you created a new directory in the root directory of that partition that you also wanted in your Home folder. That might take about 3 seconds, if you're slow.
[/LIST]
Just a thought.

---

### Post by CatKiller on 2012-07-24
> **jatwood said:**
> What about USB thumb drives or external HD? I  don't see lost+found  folders on them. The same should apply to a  separate partition. Also, I  don't see how there is a "root" directory  under this partition or any  other like an external HD or USB. It's a  device and should be mounted as  such.

I'm not sure that you've really got the hang of the filesystem hierarchy. I'll contrast it with Windows because the chances are that you're at least somewhat familiar with the way that behaves.

When you have multiple partitions in Windows, they each get a different drive letter. That is, one partition might be mounted at C: and another might be mounted at D:. The root directory of each of those partitions would be C:\ and D:\, respectively. The root directory of a partition is the one that contains everything else, be that files or sub-directories.

Let's imagine that you're using Windows and your C: partition is getting a bit full, so you want to use another partition to hold your documents and settings. You're scuppered, though, because everything want to save in C:\Docume~1\ rather than D:\whatever.

Let's also imagine that Windows wasn't made by Microsoft and so your choice of filesystem format wasn't simply between the old-and-rubbish-filesystem and the really-old-and-really-rubbish filesystem. You might instead have an option of a filesystem that's blindingly fast with a very large number of small files (say, dynamically-generated web pages) or with some insulation against sudden power loss. Or perhaps there's a server somewhere that has information you'd like to use, but when that wasn't available you'd like to use a local drive instead. With Windows you need to have a drive letter for each partition and you don't really get to pick which filesystem gets used for each task because everything assumes you want it to write to C:. And you didn't even get to choose which partition got which letter for two decades.

You still end up with directories getting created automatically on each partition (System Volume Information and Recycle Bin are the ones that I remember) because to do otherwise would be madness, but you don't get to delete them from within Windows. To see why it's not a good idea, imagine that you have a small C: drive and a large D: drive that contains large files. You "delete" a large file from the D: drive - the Ubuntu DVD iso, say. Since D: has no Recycle Bin, because there's only the one Recycle Bin and that's on C:, the file has to be copied from one partition to another, which takes some amount of time, then actually deleted from D:. You've now wasted some non-zero period and processor cycles (copies between partitions have been notoriously bad in Windows) and taken up precious space on your small C: drive, that every program wants to write to, for a file that you don't even want any more. And if you do decide that you want it after all you have to go through the whole process again.

The UNIX-like method is to have a unified filesystem hierarchy; there are no drive letters because everything is mounted somewhere under /. Directories are arranged by function. Any directory within the hierarchy can be a mount point for any filesystem. So if, say, you had a teeny-tiny SSD which is perfect for fast access to files that don't change very often then you might choose to mount that at /boot. If you had a large hard drive you might put your /home on it. You might want your /var/www to be a different filesystem to the rest of the machine. If you wanted to have some kind of thin client, you might have /usr and /var on a network machine. And so on. It's all very flexible.

---

### Post by redmk2 on 2012-07-24
> **CatKiller said:**
> Allowing the directories that you don't want to see to be created and automatically deleting them. redmk2 has said that he does this. 
Nope, I clear the the.Trash folders on multiple partitions with a single script.  I don't delete the various .Trash folders themselves.

It's a waste of time to worry about something that is working correctly anyway.  I never mount partitions in the /home filesystem for some of the reasons you mention.  like you say, it's trivial to mount the partition outside of /home at something like /data and then only link to the subdirectories of /data back to home.  Something like this works```
/data
/data/pictures
/data/videos
/data/documents
/data/downloads
```
... but then, why the paranoia of intermixing the data in the users home directory with what Ubuntu puts there by default.  I don't get it.  There's nothing mysterious about the default directories.

[COLOR="Blue"]Edit:[/COLOR]>  mount your partition somewhere else (/mnt/something would be the usual place) and then symlink the directories in that partition to directories in your Home folder.[COLOR="Blue"]If you hard link these then they will act like you have the data at both places when it exists only at /data/<somewhere>.  The beauty or that is that you can't truly delete (unlink) the files unless you delete it from both locations.  It will however be unlinked from the first while continuing to be linked at the other location.  See the man pages for *link*.[/COLOR]

---

### Post by jwbrase on 2012-07-25
> **jatwood said:**
> What about USB thumb drives or external HD? I don't see lost+found  folders on them.

That's because flash drives are usually formated with FAT32, and I'll wager all the external hard drives you've used were formatted with NTFS. I can attest that I have seen lost+found folders on flash drives I've formatted with ext2 or ext3.

> 
That's an awkward workaround don't you think? So I can't delete anything on that partition unless I use a bash command like rm.

Compared to just ignoring the Trash folder, yes. I don't think you'll find *any* modern operating system with a GUI that doesn't have one (Windows has the Recycle Bin, and I'm fairly certain that OS X has a trash folder too). Now, I'm not sure that every such operating system stores its trash folder in the root directory of a partition, but I'm pretty sure that they all have one.

And a trash folder can really be a lifesaver. I've changed my mind on files I had previously deleted --- and been lucky enough to find them still in the trash --- any number of times.

> **CatKiller said:**
> You still end up with directories getting created automatically on each partition (System Volume Information and Recycle Bin are the ones that I remember) because to do otherwise would be madness, but you don't get to delete them from within Windows. To see why it's not a good idea, imagine that you have a small C: drive and a large D: drive that contains large files. You "delete" a large file from the D: drive - the Ubuntu DVD iso, say. Since D: has no Recycle Bin, because there's only the one Recycle Bin and that's on C:, the file has to be copied from one partition to another, which takes some amount of time, then actually deleted from D:. You've now wasted some non-zero period and processor cycles (copies between partitions have been notoriously bad in Windows) and taken up precious space on your small C: drive, that every program wants to write to, for a file that you don't even want any more. And if you do decide that you want it after all you have to go through the whole process again.


There's an even easier way to explain why you need a separate trash or lost and found folder for each partition:

You're away from home and don't have your computer with you. You visit an Internet cafe (or your aunt's or friend's house) and plug your flash drive into one of the computers there. In the process, you decide to delete a file. A week later you're working on your computer and decide you still want the file. If the machine you used has an operating system that only keeps one global trash directory on the OS partition, your file was copied to that directory when you deleted it, and you can't access it from your machine. If the OS keeps a trash directory on every partition, deleted files from a given drive stay with that drive, and you still have your file.

A similar argument applies to lost+found.

---

### Post by jatwood on 2012-11-13
I think that I've found a simple workaround for now...both in Nautilus and PCManFM.

As I originally suspected, nautilus **is** recreating the lost+found and the trash folders. I'm currently using PCManFM now to handle delete and copy operations. I find it much faster and less resource-hungry than nautilus anyway, plus it doesn't create the lost+found folders and trash folders when I want to delete something. When it deletes something, it really deletes it! It's great. I was frustrated with nautilus because it would send anything and everything deleted from my partition to the trash, including a large debian image file that I had stored...not something I want to do. This was from using the 'delete' key on my keyboard, not the 'move to trash' command. Nautilus does have an option to delete things directly, but you have to right-click and select delete.  I would also have problems using rsync when the lost+found folder wouldn't allow copy operations. So yea, this was a ridiculously simple fix.

Looking back at the original responses it's amazing to see the amount of resistance and backlash from people when asking about this. I didn't see the big deal about eliminating the lost+found/trash from a partition. To some people this was like a radical idea from another planet...heresy really ;)

Nevertheless I have the results that I want, and I'm thinking about switching from nautilus to PCManFM altogether (for other reasons too). I think making the switch will require me to exclusively use Lubuntu or Debian though.

---

### Post by JKyleOKC on 2012-11-13
You might give Xubuntu a try; its file manager is Thunar, which is quite a bit lighter than Nautilus, and which provides shift-delete to immediately delete anything, and ordinary delete to move things to "trash." The options work both with the delete key, and with the delete choice from the right-click context menu.

---

