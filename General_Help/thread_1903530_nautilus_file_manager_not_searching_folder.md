---
title: "nautilus file manager not searching folder"
date: 2012-01-02
forum: General Help
---

### Post by chrisc200 on 2012-01-02
On 11.10
I have a folder called "DATA" in my home directory

When I use nautilus to search for files, it doesn't find any files at all in this directory.

The permissions all look good and owned by me.

Why is this? known issue? I cannot find any reference to it.

---

### Post by Paddy Landau on 2012-01-03
Please open a terminal and enter the following two commands. Post the results here.
```
ls -ld ~/DATA
ls -lA ~/DATA
```

---

### Post by chrisc200 on 2012-01-04
here you go:

chris@chris-ThinkPad-T420:~$ cd ~
chris@chris-ThinkPad-T420:~$ ls -ld ~/DATA
drwxr-xr-x 9 chris chris 4096 2012-01-03 15:18 /home/chris/DATA
chris@chris-ThinkPad-T420:~$ ls -lA ~/DATA
total 72
drwxrwx---  5 chris chris  4096 2011-10-30 08:16 Athens
drwxrwx--- 12 chris chris  4096 2011-11-13 14:46 PROJECTS
drwxrwx--- 22 chris chris  4096 2011-11-01 23:46 SOFTWARE
drwxrwx--- 11 chris chris 20480 2012-01-03 15:17 TECH_TIPS
drwxrwx---  2 chris chris  4096 2011-11-03 16:35 UBUNTU-UTILS
drwxrwx---  9 chris chris  4096 2011-10-30 08:17 Wedding_pictures_good
drwxrwx---  6 chris chris 32768 2011-10-30 08:17 Wedding_songs

---

### Post by chrisc200 on 2012-01-04
I have no idea why, but it suddenly works now.

In the meantime I did do a software update and reboot.

I don't know why it didn't find files in there previously.

---

### Post by Paddy Landau on 2012-01-04
> **chrisc200 said:**
> I have no idea why, but it suddenly works now.
Oh, well, we'll have to chalk it up to experience!

Sometimes, I have found that Nautilus can be a little behind; perhaps reading from its cache. So, I guess that might have been the problem.

If you're happy, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

