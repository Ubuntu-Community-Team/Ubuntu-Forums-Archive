---
title: "Erase all files within a directory from Command Line?"
date: 2009-12-11
forum: General Help
---

### Post by thebrotherofasis on 2009-12-11
Hello,

From the command line, how can I delete all the files while standing inside a directory?

For example, if i am in ~/Downloads/ what command can I use to remove all the **files** from within that directory, **without** deleting the Directory itself as would be the case of

```
rm -r ~/Downloads
```

---

### Post by lyall on 2009-12-11
go to the help section
click on System then select Help and Support
search for rm
click on Using the command line

3.6.&#8195;rm
rm is used to delete files.

rm foo

deletes the file foo from the current directory.
      
By default, rm will not remove directories. To remove a directory,
you must use the -R option. For example,
	
rm -R foobar

will remove the directory foobar, and all of its contents!


I try to look in the help section  and searching the forums to get answer

good luck and have fun learning

---

### Post by sgosnell on 2009-12-11
To remove all files in the current directory, use 'rm *'.  If there are subdirectories, they won't be touched, but all files in the current directory will be removed.

---

### Post by bodhi.zazen on 2009-12-11
if you are in downloads, 

```
rm -rf ./*
```

just take care as that command will delete without asking confirmation, so use with caution (many people have wiped whole systems with minor typos ;).

---

### Post by thebrotherofasis on 2009-12-12
> **bodhi.zazen said:**
> if you are in downloads, 

```
rm -rf ./*
```

just take care as that command will delete without asking confirmation, so use with caution (many people have wiped whole systems with minor typos ;).

Right, that's exactly what happened to me :( two days ago...

The thing is I am trying to create a script that will backup some directories and send them to my email, but I am rather new to linux bash scripting.

Here's my script:


```
#!/bin/bash

filename=$(date '+%y_%m_%d')_"backup.tar.gz"
backupdirs=~/Documents/PLC/Databases/

tar -cpzf ~/Backups/$filename $backupdirs

echo "PLC 4.1 database automated backup completed successfully" | mutt -s "4.1 Backup "$filename -a ~/Backups/$filename -- myemail@myemail.com

```

So, so far the script seems to be working perfectly. However, it is cumulating many files under ~/Backups and I would like to make the script clean the directory ~/Backups every time it is executed so that the backups are kept in my email rather than locally.

And two days ago I was playing with the * option, when ooops! it accidentally wiped out my home directory :oops::shock:

Now, I will try to do this, but before, can anyone confirm that it will not delete other than my ~/Backups/ directory files again?


```
#!/bin/bash

filename=$(date '+%y_%m_%d')_"backup.tar.gz"
backupdirs=~/Documents/PLC/Databases/

[COLOR="Red"]rm -rf ~/Backups/*[/COLOR]

tar -cpzf ~/Backups/$filename $backupdirs

echo "PLC 4.1 database automated backup completed successfully" | mutt -s "4.1 Backup "$filename -a ~/Backups/$filename -- myemail@myemail.com

```

Thanks in advance!

---

### Post by Some Penguin on 2009-12-12
If you're feeling paranoid, you could change the * to *.gz.

I'll note that 

1) you could use the 'find' command to be more selective, e.g. deleting files which are so-and-so old, and

2) if the files that you're backing up this way could be changing during the backup, then you run the risk of inconsistency.  Schedule your jobs carefully.

3)  It might be a good idea to log the results of the tar command and include them in the e-mail, just in case there's a problem.

---

### Post by thebrotherofasis on 2009-12-12
> **Some Penguin said:**
> If you're feeling paranoid, you could change the * to *.gz.

I'll note that 

1) you could use the 'find' command to be more selective, e.g. deleting files which are so-and-so old, and

2) if the files that you're backing up this way could be changing during the backup, then you run the risk of inconsistency.  Schedule your jobs carefully.

3)  It might be a good idea to log the results of the tar command and include them in the e-mail, just in case there's a problem.

Thank you for your notes.

I will look into all of this. Thank you.

---

### Post by thebrotherofasis on 2009-12-12
> **bodhi.zazen said:**
> if you are in downloads, 

```
rm -rf ./*
```

just take care as that command will delete without asking confirmation, so use with caution (many people have wiped whole systems with minor typos ;).

What does " ./ " mean, or do?

---

### Post by bodhi.zazen on 2009-12-12
> **thebrotherofasis said:**
> What does " ./ " mean, or do?

. = current directory

.. == one directory above.

---

