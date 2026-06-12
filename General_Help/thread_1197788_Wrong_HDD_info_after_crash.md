---
title: "Wrong HDD info after crash"
date: 2009-06-26
forum: General Help
---

### Post by ICDeath on 2009-06-26
Hi, guys. I'm using Ubuntu 9.04 and ext4 filesystem. It crashed for the first time when I deleted 4 big files with a total size of 55Gb (or around that). I noticed in the lower left corner it stated the correct free space after the deletion. After I hard-rebooted the space was back to what it was WITH these files however they are not in the system anymore and not invisble either (I did ctrl+H). Dunno whether it is important but I shift-deleted them. Is there anything to do to tell the system it has calculated wrong? I don't want to just give up on 55Gb, duh. 

Here is a screen of proof.

---

### Post by jimv on 2009-06-26
Which sub-directory in your home folder were these files in?  Can you run this command in that directory from a terminal and post the output here?

```
ls -laSh
```

---

### Post by ICDeath on 2009-06-26
They were in the Videos subdirectory. Here's what ls -laSh gives:

```
smirk@smirk-laptop:~$ ls -laSh /home/smirk/Videos
total 8.0K
drwxr-xr-x  2 smirk smirk 4.0K 2009-06-26 22:17 .
drwxr-xr-x 50 smirk smirk 4.0K 2009-06-27 02:01 ..
```

---

### Post by siryuhan on 2009-06-26
The problem you're facing right now probably stems from the way ext4 journals, and is something that is supposed to be changed in 2.6.30 but is still very buggy. If this is the case, I'm not aware of anything you can do about it (short of reinstalling, that is).

Of course, it could be another issue altogether. Either way, I would highly recommend switching back to ext3 for now.

---

### Post by ICDeath on 2009-06-26
So much for using Ubuntu for 2 days :( Ouh well, seems it's all pointing to a reinstall.

---

### Post by jimv on 2009-06-26
If you haven't done the reinstall yet, try 

rm -rf /home/smirk/Videos

---

### Post by ICDeath on 2009-06-27
> **jimv said:**
> If you haven't done the reinstall yet, try 

rm -rf /home/smirk/Videos

That worked! It now shows the correct space. Thx a lot for help guys. This problem is solved.

---

