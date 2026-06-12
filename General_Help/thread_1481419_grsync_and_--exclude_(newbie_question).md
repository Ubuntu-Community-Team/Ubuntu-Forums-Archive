---
title: "grsync and --exclude (newbie question)"
date: 2010-05-12
forum: General Help
---

### Post by worldhello on 2010-05-12
Hi,

I'm new to linux and I have question about backup. I'm running karmic on a 64 bit deskttop and a 32bit netbook. I used grsync a couple of times to backup /home/ and it worked perfectly. Now I'd like to exclude a couple of directories and I ran into problem: based on several postings on the forum, I created a file

  /home/(user)/.grsync/exclude

that contains the path

  /home/(user)/prog/bad

and then in the grsync dialog box, under `advanced options' I added

  --exclude-from=/home/(user)/.grsync/exclude

but grsync still backed up the directory I thought I excluded. I had tried a few other variations, including

* adding double quotes around the path in the exclude file and/or the exclude-from command;

* adding extra double-quotes at the end of the path in the excluded path

* removing /home/ from the path and/or the --exclude-from command;

* instead of using an exclusion file, used directly the command --exclude=/home//prog/bad (with or without double quotes and/or /)

I must have missed something trivial; your comments and suggestions are most welcome!!  

(note: I had inadvertently posted this as a reply to another thread; newbie mistake...)

---

### Post by x C0MMAND0 x on 2010-05-12
I have

--exclude-from /home/user/exclude.txt

You have 

--exclude-from**=**/home/user/exclude.txt

Try without the = sign maybe?

---

### Post by worldhello on 2010-05-12
> **x C0MMAND0 x said:**
> I have

--exclude-from /home/user/exclude.txt

You have 

--exclude-from**=**/home/user/exclude.txt

Try without the = sign maybe?

 Thanks -- but it does not work for me :-(

---

### Post by komputes on 2010-10-11
You can add --exclude-from=".grsync/exclude" in the Additional Options (field) in the Advanced Option (tab)

In the exclude file put the name of each subdirectory (one per line) that you would like to exclude. Example:
```
.thumbnails
Downloads
```

I have found that you can't put a full path like in your example:
```
/home/(user)/prog/bad
```

If you hare backing up /home/(user), then you must only put the tail end of the path in the exclude file. This is the only way it will work:
```
prog/bad
```

---

### Post by ufugu on 2010-10-14
I use something like --exclude /home/(user)/.grsync/exclude/*

It copies the name of the directory, but none of the enclosed files.  Would that work for your scenario?

---

### Post by DeMus on 2010-10-14
The man pages (man rsync) gave this:

```
--exclude-from=FILE
This option is related to the --exclude option, but it specifies
a FILE that contains exclude patterns  (one  per  line).   Blank
lines  in  the  file  and  lines  starting  with  ’;’ or ’#’ are
ignored.  If FILE is -, the list  will  be  read  from  standard
input.
```

So if this is what you have typed then it should be the file itself you use to exclude items.
For more info type man rsync in a terminal and start reading. This program has a very long list of possibilities .

---

### Post by AndresC on 2011-07-08
I am using /home/ as source destination and

--exclude=*/.cache

in the advanced options,

and so far dry-run does not copy the .cache directory...

---

