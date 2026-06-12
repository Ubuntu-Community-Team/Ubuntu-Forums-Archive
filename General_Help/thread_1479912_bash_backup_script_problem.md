---
title: "bash backup script problem"
date: 2010-05-11
forum: General Help
---

### Post by sevenearths on 2010-05-11
On our server at work I have two scripts that run daily and monthly backups.

```
find . -type f -print0 | xargs -0 mv -t $DIRNAME
```

Currently the following line moves all files from the root and all subdirectories to one directory (in this instance 'Apr_10', which basically means it moves ALL backups into ONE folder). How can I change it so it only moves files found in the root folder (not the sub folders)?

ADDITIONAL:

I'm in the directory I need to be in and basically I just need to move all the files that have been backed up over the month in that directory (not sub-directories) to another date indexed folder. Maybe I need another command!

---

### Post by dandnsmith on 2010-05-11
Looks like you need to truncate the find - I forget the parameter, but you can say 'limit the search to the current directory'.

The next stage, you need to search based on (something like) creation date/ modification date/access date - not sure I understand the precise parameters of your problem - and then move the results into the other folder.

Yes - I'd use a new command for that

---

### Post by Razzie on 2010-05-11
find . -maxdepth 1 -type f -print0 

then it will only search the current directory and wont go into folders

---

### Post by sevenearths on 2010-05-13
Thanks. Nice 1!

=D>

---

