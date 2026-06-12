---
title: "General backup question!"
date: 2009-11-19
forum: General Help
---

### Post by stevenwilliamsen on 2009-11-19
Hello all! I've been using grysnc to back up one external hard drive to another. The problem is, external hard drive #2 is smaller than external hard drive #1. How can I sync everything from #1 to #2, but leave out one specific folder that has a lot of data I don't need? I am comfortable with CLI, I just use grysnc because I'm lazy sometimes.

---

### Post by undecim on 2009-11-19
never used grsync, but I'm going to go out on a limb and say that it's probably a frontend to rsync. You should be able to use the --exclude option. Take a look at the rsync manual.

---

### Post by ajgreeny on 2009-11-19
Yes use rsync instead.  If you're not certain of the command to use, do a simulation first in grsync, and note the command shown in the dialog box.  Then use that command, without the -n option and with the --exclude option, and you will get the exact same transfer, but without the pathways you show in --exclude being moved.

---

### Post by XCan on 2009-11-19
rsync can read all kinds of filters from a text file. However, it seems that you're only wanting to exclude one single folder thus I would just jam the --exclude flag into the command like
```

rsync -avz --delete /home/user/files /path/to/backup --exclude=user/excluded_dir

```

Beware of the backslashes!

---

### Post by worldhello on 2010-05-11
Hi,
I'm new to linux and I have question about backup.  I'm running karmic on a 64 bit desktop and a 32bit netbook.  I used grsync a couple of times to backup  /home/<user> and it worked perfectly.  Now I'd exclude a couple of directories and I ran into problem:  based on several postings on the forum, I created a file

/home/<user>/.grsync/exclude

that contains the path

/home/<user>/prog/bad   

and then in the grsync dialog box, under "advanced options" I added

--exclude-from=/home/<user>/.grsync/exclude

but grsync still backed up the directory I thought I excluded.   I had tried a few other variations, including

  * adding double qoutes around the path in the exclude file and/or the exclude-from command;
  * adding extra "/" at the end of the path in the excluded path
  * removing /home/<user> from the path and/or the --exclude-from command;
  * instead of using an exclusion file, used directory the command   --exclude=/home/<user>/prog/bad  (with or without double quotes and "/")

I must have missed something trivial; your comments and suggestions are most welcome!!

---

