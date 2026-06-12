---
title: "Delete files recursivly  but preserve directories"
date: 2009-10-15
forum: General Help
---

### Post by confused_user on 2009-10-15
Hi, i need to run a monthly delete script to remove all files recursivly.  But i dont want to delete the directories.

Any ideas?

---

### Post by Idefix82 on 2009-10-15
You can use the find command. For example
```
sudo find /full/path/to/folder -type f -delete
```
will delete all files (that's what -type f does) that it finds in /full/path/to/folder and all subfolders. If you want to first test that it's doing the right thing, run
```
sudo find /full/path/to/folder -type f -print
```
first. It will print all the files that match your search, instead of deleting them. Have a look at
```
man find
```
for a huge number of options and some examples.

---

### Post by HNS-I on 2009-10-15
First thing that comes to mind is use find to search for regular files and use -exec to delete the match.

find /path/to/basedir/ -type f -exec rm {} \;

Maybe you can test with ls in stead of rm first to be sure that it works for you.

---

### Post by confused_user on 2009-10-15
Thanks guys,

I should expand a little on what i'm trying to acheive i think.

so i have a file server, each month i want to delete the files in it but preserve the directories 

/files/user1/my.stuff/loadsoffiles*
/files/user1/random/projects/loadsoffiles*
/files/user1/random/midgetporncollection/loadsofiles*

So i'd liek to delete any and all files underneath /files/user1/ but preserve the directories and subdirectories 

so i would still be left with the original directory structure intact but not files

Make sense?

I think using the find exec will not do this unless i run it on each directory individually?

---

### Post by HNS-I on 2009-10-15
Find exec will run with all matches under the specified directory, although using -delete is cleaner.
You can put this command in a bashscript and put that in /etc/cron.monthly/
All scripts in that directory will be run by cron as specified in /etc/crontab. You could change the day of the month in crontab if you like.

---

### Post by confused_user on 2009-10-15
Ahh yes, so it does, yeah that wors fine for me.

I should have worked that out for myself since i'm using find /path/to/basedir/ -type f -exec rm {} \; in the same script for getting rid of old log files

Thanks for your help!

CU

---

