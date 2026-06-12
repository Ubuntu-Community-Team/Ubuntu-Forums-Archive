---
title: "how do you list all files in drive with file sizes?"
date: 2011-07-17
forum: General Help
---

### Post by fuzzylogic25 on 2011-07-17
Usually I like to keep a list of all the files in a drive so I know which file is in what drive.

I do this simply by going into the required drive in the terminal (/media/BACKUP01/) then i type the command "find . > BACKUP01.txt".

But all this does is list every file in every folder and sub-folder. Is there a way to also have it display the file size next to it?

---

### Post by Zebediah49 on 2011-07-18
```

du -ah > list_of_files.txt

```

should do what you're looking for.

EDIT: Sorry, that'll just do directories.  Needed to add the -a option.

---

### Post by DawieS on 2011-07-18
The **du** command returns the file size on disk, and may include the size of gaps between segments, if the file is written with more than 1 segment. Generally it is larger than the actual file size. It may also vary depending on the position of the file on the disk, and multiple copies of the same file may return different numbers.

The **ls** command will be better to use in this case, and returns the actual file size. There are various sorting and other options, for example:
**ls - Rgo** will show columns with permissions, size, date, time and filenames, sorted alphabetically.
**ls - Rtgo** will show the same, sorted by modification time.
**ls - RSgo** will show the same, sorted by size.

For more information type **man ls** in a terminal.

---

### Post by NoFriends on 2011-07-18
Thanks, Helped.

---

### Post by fuzzylogic25 on 2011-07-18
thanks for the help! The problem I have left is the format of the display. What I would like is something like the following:

---------------------------------------------------
/media/D/Backup/Projects/proj1.zip    23KB
/media/D/Backup/Projects/proj2.zip    11KB
/media/D/Backup/Projects/essay.doc    12,043KB
---------------------------------------------------

But with the ls function, it turns out to be something like:

---------------------------------------------------
/media/D/Backup/Projects/: 
total 220MB
proj1.zip  23K     proj2.zip  11K   essay.doc    12MB
---------------------------------------------------

Is there anyway of changing the format directly above to the one above that?

---

### Post by Wayne_V on 2011-07-18
You could just do:

find . | while read f; do du -h "$f" ; done

or, if you really wanted the filename first:

find . | while read f; do echo -e "$f \t `du -h \"$f\" | awk '{print $1}'`" ; done

or even better,  save a full listing:

find . -ls

I forgot, linux find also has the -printf option:

find . -printf "%p\t%kk\n"

---

### Post by oldos2er on 2011-07-18
How about ```
ls -Ral > file.txt
``` ?

---

### Post by fuzzylogic25 on 2011-07-20
That also works too! Thanks!

I think it has come to a point where I will need to just make a bash script, when i learn more about linux commands.

I wanted to ask for another question, I would also like to know the sizes of every folder. Now currently, using the ls -R... commands work and show the folder sizes but it doesnt include subfolders.

for example if we had:
/Data/
/Data/1
/Data/1/10
/Data/2

The size of /Data/ does not include the files in the sub folders. So to get a total of /Data/ I would have to calculate ths sizes of all sub folders. /Data/ is just showing the size of the folder links I think. Not the sizes of those folders.

So how can we get a list of folders showing the total size for each folder (including the subfolder sizes)?

---

### Post by Niocora on 2011-07-20
Have you tried

ls -lh


?

---

### Post by Wayne_V on 2011-07-20
find . -type d -maxdepth 1 -exec du -sk {} \;

will give the approximate size of each top level directory.   leave off the -maxdepth option if you want to sum each subdirectory as well.   also, you might want to review the symlink  and mount options in 'man find'

---

