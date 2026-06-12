---
title: "[bash] sudo -S problem after install of 10.04"
date: 2010-08-04
forum: General Help
---

### Post by phdb on 2010-08-04
Hi,

I had some bash scripts on Ubuntu 09.10 (mint version) that fail to work on Ubuntu 10.04.

The line that fails is the following:
```
# cat file_with_my-password.txt > sudo -S something
cat: invalid option -- 'S'
Try `cat --help' for more information.
```
In my case "something" mounts some filesystems (that fail to load from fstab - bios "fake" raid 10), but I get the same error for any sudo command.

It is the **same** script that used to work under 09.04 :-/

Any help highly appreciated!

Ph.

---

### Post by sisco311 on 2010-08-04
It's:
```
cat file_with_my-password.txt | sudo -S something
```
You have to pipe the password to sudo instead of redirecting the output of cat to the *sudo* file. ;)

But storing your password in a plain text file is a huge security risk. I would suggest you to edit the sudoers file & allow your user to run the specific command without a password. 

[thread=1132821]HowTO: Sudoers Configuration[/thread]

---

### Post by phdb on 2010-08-05
Hi, thanks for the answer.

that gives another error message ```
bash: line 1: *****: command not found
```(in the place of the the five stars is the password)

I guess that your suggestion about sudoers is anyhow the way to go (although very strange that this stopped working, isn't it?)
I will report later if it works, because I want the command to be executed always before the user  (person) can do something. --> it goes in /etc/init.d

---

