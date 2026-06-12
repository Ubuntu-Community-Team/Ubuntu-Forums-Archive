---
title: "Unison - Failed to set permissions"
date: 2010-05-19
forum: General Help
---

### Post by lallalla on 2010-05-19
I recently changed the ownership of files on my internal harddrive from 'username' to 'root'. Ever since Unison fails to synchronise files between my internal drive and the external drive. Owner of files in external harddrive is 'user name' and not 'root'. Both harddrives are in NTFS format.

The error message:
Failed to set permissions of file /media/External Disc/....... to ???rwxrwx: the permissions was set to ???------ instead. The filesystem probably does not support all permission bits. You should probably set the "perms" option to 0o0 (or to 0 if you don't need to synchronize permissions). 

I added perms=0o0 and also tried perms=0 
but both failed

I should add that files created after changing ownership do synchronise without problems

any ideas? Many thanks

---

### Post by f251 on 2010-06-23
In this case, you should append the option "perms = 0" into the config file. For example, i am assuming you are using default profile, open the config file located at "~/.unison/default.prf" (i am using Ubuntu), then add the above option. Then it should work.

---

### Post by dcstar on 2010-06-24
> **lallalla said:**
> 
..........
I should add that files created after changing ownership do synchronise without problems

any ideas? Many thanks

I don't think you cannot sync the same file after you do something like this.

It would be better to delete that original Unison profile and create a fresh one so all the files are synced from the original source again.

---

### Post by ctmccaw on 2011-02-01
Just an additional note (from a newbie, so no guarantees about its validity or insight):

Upon syncing a Windows Briefcase on a USB memory stick with a local directory on my Ubuntu machine with Unison, I received the same error as quoted above.

I went and found the relevant configuration file (.prf) in my home directory, under the (hidden) .unison subdirectory. It looks something like this:



```
# Unison preferences file

root = /media/shared_data/xxx
root = /media/FC25-31F7/xxx
```


At first I added the "perms = 0" option as the **final line** to the file, but the error persisted. :mad:

I then moved the "perms = 0" option **before the description of the root directories** so it looked like this:


```
# Unison preferences file

perms = 0
root = /media/shared_data/xxx
root = /media/FC25-31F7/xxx
```


...and the problem was solved.:p

Maybe this should have been obvious, but I was certainly happy when I discovered it worked!

C

---

### Post by lallalla on 2011-02-01
:)

---

### Post by wolterh on 2011-08-31
Hm, I bet you didn't restart the application after the first change, because I was able to add it to the end of the file and it did work.

---

