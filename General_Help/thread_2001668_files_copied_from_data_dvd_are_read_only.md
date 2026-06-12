---
title: "files copied from data dvd are read only"
date: 2012-06-11
forum: General Help
---

### Post by black veils on 2012-06-11
i use thunar, i tried the GUI way of changing permissions recursively, but that won't work, or only on a couple of files.

i tried doing the command line way also, with same results.

its the same with different dvd or cd discs.

i have dropbox installed, but i may have had the problem before that.

i use k3b, have tried both linux only format for disc, and windows friendly format, doesn't make a difference.

any ideas as to why this is happening, and so stubbornly?  surely it is not this way for everyone?

---

### Post by mcduck on 2012-06-11
That's the way it works, the filesystems used on optical media don't support POSIX ownerships or permissions, so they can't be stored with the files. And the fileystems are by design read-only, which means the files you copy back to harddrive from the media will keep the read-only permission.

You shouldn't have any troubles changing the permissions and ownership to more usable ones aftewr you have moved the fiels to your hard drive, though.

...and also a nice tip, if you use optical media (or FAT/NTFS-formatted drives) for backups or to transfer your Linux files, compress them into a .tar.gz beforehands. That way the ownerships and permissions will stay intact.

---

### Post by FatFrog on 2012-06-11
According to the website...
"From the Tools menu > "Read Only Mode". This will automatically be enabled in certain circumstances - such as opening binary files or files with encodings that it cannot handle, or when the file has lines that exceed the maximum line length setting."

---

### Post by black veils on 2012-06-11
> You shouldn't have any troubles changing the permissions and ownership  to more usable ones aftewr you have moved the fiels to your hard drive,  though.

thats the problem, i cant change the permissions unless i do one file at a time, which of course is insane.

as i said, i did the recursive thing and it doesnt work, or not for more than the initial files within one folder, it wont apply to any sub-folders.

---

### Post by Kr0nZ on 2012-06-11
open a terminal windows,
cd to the directory you copied files too
type
```

sudo chmod -R 777 /home/user/filesfolder

```
replace '/home/user/filesfolder' with the path where your files are located.

then after type 'ls -l' to verify

---

### Post by mcduck on 2012-06-11
I haven't used Thunar in ages, but chmod command in a terminal shouldn't have any troubles fixing the permissions, just use the "-R" option to change permissions recursively.

---

### Post by black veils on 2012-06-11
> **mcduck said:**
> I haven't used Thunar in ages, but chmod command in a terminal shouldn't have any troubles fixing the permissions, just use the "-R" option to change permissions recursively.


have done that, and the result is the same, yes i did proper commands. its strange, i wonder could dropbox (and the inevitable nautilus link) be the cause?

---

### Post by forrestcupp on 2012-06-11
Post for us the exact command that you typed into the terminal.

---

### Post by black veils on 2012-06-11
> **forrestcupp said:**
> Post for us the exact command that you typed into the terminal.

something like this ```
sudo chmod 754 -R /path/to/file/or/directory
```following this guideline:

first is owner
second is group
third is anyone else

Permissions:

    0 – no permission, this person cannot read, write or execute
    1 – execute only
    2 – write only
    3 – execute and write only (1 + 2)
    4 – read only
    5 – execute and read only (1 + 4)
    6 – write and read only (2 + 4)
    7 – execute, write and read (1 + 2 + 3)
   -R - means to all folders and files within

---

### Post by underquark on 2012-06-11
OK so you've told it to allow the owner read, write, execute privileges.  But are you the owner? Use
```
ls -l
```to find the owner of the files and then you might need to use chown to change owner to yourself. Or, just make them all 777 (read, write, execute for everyone).

---

### Post by black veils on 2012-06-11
using 777 seems to work, i will test some more, but that is good. i thought i had tried it before, but maybe not. this situation occurred on xubuntu 11.10 and 12.04.

thanks for the replies

---

