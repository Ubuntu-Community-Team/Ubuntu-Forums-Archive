---
title: "Recovering files from dead Mac using ubuntu live - problems"
date: 2010-09-30
forum: General Help
---

### Post by Neil B. on 2010-09-30
I have a Macbook that I need to recover files off of. Problem is that the screen is bad, and I have no way of booting the thing up to access the filesystem. So now I have the hdd plugged into a PC and have booted the ubuntu live cd. 

I can access the drive, but my pictures, music, and library folders have a red x marked over them indicating I do not have permission to view their contents. 

I have been trying to change the permissions to no avail. For some reason I cannot navigate to the directory through the terminal to change the permission. Instead, when I go to cd /media/Macintosh HD is throws a No such file or directory error.

The Macs hdd is already mounted, because I can access its file structure. 

I need to know how to get into the Macintosh HD through the terminal so I can give read/write permissions to the music and pictures folders. 

Thanks in advance.

---

### Post by mike555 on 2010-09-30
try sudo nautilus in terminal then use that nautilus (don't close terminal -till your done)

---

### Post by efflandt on 2010-09-30
Spaces can throw a wrench into specifying directories or filenames because the shell does not know if the space is part of the path or separating a list of names.   So you need to either escape spaces (with backslash \) or use quotes, or it is often easier to use bash tab completion to grab the rest of the name in the proper format.

For example if the name of the drive is actually "Macintosh HD" you could start typing **cd /media/Mac** then hit the **tab** key and it would end up **cd /media/Macintosh\ HD** assuming nothing else in that directory begins with Mac.  If you do have files or directories that begin the same, tab completion would complete what it can that is common between them, then you would have to type more characters that are unique to one of them before it could tab complete the rest of the name.

I am not familiar with Mac file systems, but you likely need to use sudo before commands to do certain things as root if it is a dir/file permission issue.  Although, that may not help if the issue is a corrupted file system (bad sectors, etc.)

---

