---
title: "NTFS files turned to folders which cannot be deleted"
date: 2011-08-28
forum: General Help
---

### Post by k98kurz on 2011-08-28
Backstory: one day, I was listening to some music in the background while playing Nexuiz on my Backtrack 5 installation (which is gnome Ubuntu based). Since it is a dual boot, I had the Windows partition mounted in order to listen to some mp3's on its file system. Nexuiz decided to freeze my screen, and so I had to crash my computer without stopping audacious and without unmounting.
I then attempted to open the mp3's in Windows and they had turned into folders, both of which contained only the file "snapshot.etl". (I have since managed to delete the snapshot.etl files while raging.) I then attempted to delete them, but there was an error deleting them. I then attempted both steps in Linux, but with the same result. I have replacement files; all I want to do is remove the corrupted file/folder whatever they are.
It appears that, somehow, there are messed up ntfs permissions on several files and folders.

Also, there is a .Trash-0 on both the Windows partition and an expensive external hard drive that simply will not go away, no matter what I do.

I am running a 64 bit HP G42-415DX laptop with manufacturer hardware.

Commands I have tried to remove mp3's:
```
sudo su
cd /media/$hddname/$path_to_music_directory
rm $file1
  rm: cannot remove $file1: Is a directory
rm -r $file1
  rm: cannot remove directory $file1: No such file or directory
cd $file1
  *works*
ls -a
  .  ..
cd ..
rm -r -f $file1
  rm: cannot remove directory $file1: No such file or directory

```
Exact same thing applies for $file2.

I am going to try running chkdsk from a Windows install disk; I will update with the relevant information afterward.

---

### Post by k98kurz on 2011-08-28
Chkdsk seems to have fixed the strange file/folder things after three tries on the W7 partition, and the .Trash-0 folders have vanished after mounting and unmounting the hard drives multiple times. I still have no clue what happened. Any suggestions as to what may have happened will be appreciated.

---

### Post by Mark Phelps on 2011-08-29
Yeah ... you dismounted the Windows partition uncleanly, leading to filesystem corruption.

This is one of the main reasons I strongly suggest that folks do NOT mount their Windows partitions in Linux.  Unclean shutdown like this, as you have discovered, can result in filesystem corruption.

---

### Post by pavi_elex on 2012-03-09
I am facing a .Trash-0 problem.
A folder name .Trash-0 is made automatically in my windows partitioned drive in ubuntu.
i am not able to delete it. I am able to rename it but when i delete it, it says:
```
**Error while deleting.**
Could not remove the folder 3798967639.
Error removing file: Directory not empty
```

I am not able to delete this directory.
Please give me a solution.

---

