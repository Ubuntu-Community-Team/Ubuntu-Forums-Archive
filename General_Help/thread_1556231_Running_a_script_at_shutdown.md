---
title: "Running a script at shutdown"
date: 2010-08-19
forum: General Help
---

### Post by welshmike on 2010-08-19
I would like to run a script at shutdown that makes a backup copy of one or more of my files.
How may I do this please?
I've tried to do it as follows:
put a script Sds.sh in /etc/rc0.d
```

#! /bin/sh
# Provides:  shut down script Sds.sh at run level 0 shutdown

cp /home/mike/test.txt /home/mike/testcp.txt

exit

```

---

### Post by Yarui on 2010-08-19
That should work just fine.  I don't think you really even need the exit line.  Your problem is most likely that you didn't make the file executable after creating it.  You can do that by moving to the directory with the script in the terminal and entering the following command.

```
chmod +x scriptname
```

Replacing scriptname with whatever the name of your script is, of course.

---

### Post by dcstar on 2010-08-19
> **welshmike said:**
> I would like to run a script at shutdown that makes a backup copy of one or more of my files.
..........

Good luck, the super-fast shutdown that is built into the Ubuntu systems now makes it really difficult to do anything like that any more.

Older Ubuntu systems used to wait for processes to end gracefully, now things get chopped off at the knees for the sake of rapid shutdowns.

---

### Post by john newbuntu on 2010-08-19
I think the downside to naming it as Sds.sh is that it will get run in the end after the filesystems come down(i.e, the copy will never happen).  You might want to push it up the order and call it something more meaningful and with a lower job number such as "S05bkp" or something like that.  You could use update-rc.d if you are comfortable with it or symlink it manually.
Just a thought..  Have you tried to use Ubuntu One or dropbox to automatically sync those files?

---

### Post by Yarui on 2010-08-19
> **john newbuntu said:**
> Have you tried to use Ubuntu One or dropbox to automatically sync those files?
This is a good suggestion, assuming that the total size of all the files that need to be backed up is small enough to fit in a dropbox or ubuntu one account.

---

### Post by welshmike on 2010-08-20
Yarui,

Many thanks. I tested the script while Ubuntu was running using bash.
chmod +x was indeed needed to make it executable at shut down time.

---

### Post by welshmike on 2010-08-20
dcstar,

Thanks.
When the script ran, the shutdown was so fast that a test echo of some 256 characters whizzed by in a blink of an eye on my monitor.

---

### Post by welshmike on 2010-08-20
john newbuntu,

Thanks for the trip. I renamed the script to S01Sds.sh.

I don't fancy putting a backup of my private (financial) data out in the Cloud so it will be backed up to my external hard drive.

---

