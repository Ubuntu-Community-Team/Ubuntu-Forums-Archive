---
title: "Split big file size into small file size"
date: 2010-06-10
forum: General Help
---

### Post by rudysuryanto on 2010-06-10
Are there software that can split big file size into small file size in Linux? Thank's.

---

### Post by colorlessprism on 2010-06-10
are you asking about TAR? simply use the split command. More information can be found in the man pages of split, use "man split" in a terminal to read. make sure you keep these archives all together in a directory you label for extraction at a later date. Once the archives are split to a desirable size, they can be burned one at a time to disc.

To Split During Creation:
tar -cvpz <put options here> / | split -d -b 3900m - /name/of/backup.tar.gz. 
To understand what is going on, we will dissect each part of the command.
tar - is the command that creates the archive. It is modified by each letter immediately following, each is explained bellow.
c - create a new backup archive.
v - verbose mode, tar will print what it's doing to the screen.
p - preserves the permissions of the files put in the archive for restoration later.
z - compress the backup file with 'gzip' to make it smaller.
this is then piped (|) to the split command.
-d - This option means that the archive suffix will be numerical instead of alphabetical, each split will be sequential starting with 01 and increasing with each new split file.
-b - This option designates the size to split at, in this example I've made it 3900mB to fit into a FAT32 partition.
- - The hyphen is a placeholder for the input file (normally an actual file already created) and directs split to use standard input.
/name/of/backup.tar.gz. Is the prefix that will be applied to all generated split files. It should direct to the folder you want the archives to end up. In our example, the first split archive will be in the directory /name/of/ and be named backup.tar.gz.01 

To Reconstitute the Archive
Reconstructing the complete archive is easy, first "cd" into the directory holding the split archives. Then simply use "cat" to write all the archives into one and send over standard output to tar to extract to the specified directory.

cat *tar.gz* | tar -xvpzf - -C /  
The use of * as a wild card before and after tar.gz tells cat to start with first matching file and add every other that matches, a process known as catenation, how the command got its name.
Afterwards, it simply passes all that through standard output to tar to be extracted into root in this example.

Originally located, along with more information on TAR can be found: "[HERE]("https://help.ubuntu.com/community/BackupYourSystem/TAR")"

---

