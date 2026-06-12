---
title: "Clean up by date"
date: 2010-07-04
forum: General Help
---

### Post by new_tolinux on 2010-07-04
Hi,

I have some script running. It places folders with files in /var/tmp
The problem is that the script doesn't clean up properly and I can't predict the names of the folders.

What I'm looking for is a simple bash script I can use to clean up that folder by using a cron-job. Let's say delete everything inside folders which are 5 days or older.
I know that can be a problem since rmdir is for folders and rm for files, but I've installed secure-delete to solve that, because it's capable of removing folders with files in them.
So I need something that puts the right folder names into this command:

```
srm -drzvll /var/tmp/[folder name]
```

Used version: mythbuntu 9.04 (9.10 didn't work, didn't try 10.04 yet).

---

### Post by Will Shackleton on 2010-07-04
Hi,

For removing folders with files in, use 'rm -R [folder name]', and to run a command to get the file name, use something like this:
```
rm -R /var/tmp/`other command`
```
Note the backticks, ie ` not '. This runs 'other command', and copies the output into the outer command (rm -R /var/tmp/...).

---

### Post by new_tolinux on 2010-07-04
Thanks, but I don't know the folder names.
Actually, the deleting part was kind of solved, I only need the correct input to select the folders that can be deleted.

---

### Post by new_tolinux on 2010-07-05
bump

---

### Post by Penguin Guy on 2010-07-06
Try somethign along the lines of this, but be careful with it:
```

find /var/tmp/ -mtime +5 -exec rm -R {} \;

```

---

### Post by new_tolinux on 2010-07-06
That seems to do the trick.
I had to test it with -mtime +0 since I had manually deleted all the files a few days ago (0 free space left on the drive) and -mtime +5 didn't do anything.

Before I put it in a daily script, I ran this line from the prompt:
```
find /var/tmp/ -mtime +0 -exec rm -R -i {} \;
```
It only processed the folder created before yesterday, so +5 (and without the -i) should be more or less a secure way to tell that the files can really be deleted since the conversion script which create the files/folders takes at most 24 hours to complete the conversion.

I'll mark this thread solved.

---

