---
title: "Second hard drive - permission denied"
date: 2009-10-01
forum: General Help
---

### Post by mario_ramalho on 2009-10-01
This is kind of a long story, but i'll try to make it short. I have 2 hard drives, one used to have Win XP Pro, and in the second, i installed Ubuntu Jaunty 9.04, using Wubi. Later, my XP instalation went bad, and since the system is about 10 years old, i decided to just go with Jaunty, so i installed it in the hard drive that had Win XP in it. Later, i formatted the second hard drive with gparted, in the same format as the OS drive, (ext3), and repartitioned the whole thing as Primary, but it now tells me that i have no permissions to write to that drive, all i can do is basically look at it. I am the single user of the system, but since I'm new to Linux, I'm totally lost as to what to do to be able to use this second hard drive as additional storage. In the properties, under the Permissions tab, it shows the Owner and Group as "root", and SELinux context and Last changes are "unknown". Not sure what this means. At the bottom says "You are not the owner, so you cannot change these permissions". I was under the impression that formatting a hard drive would erase everything in it, but it's showing a folder called "lost+found" in the root of that drive. Not sure if that's standard, either. I'd appreciate any advice or help in this matter. Thank you.

Mario

---

### Post by akakingess on 2009-10-01
I am not an expert in this arena, but could you try something like
```
sudo chown username /dev/sdb1
```
obviously replacing "username" with your username and the /dev/sdb1 to whatever the other drive is according to your system.  I am not sure if that is the exact command or not, but it is something similar, hopefully someone will see my sorry attempt to assist you and correct it or confirm it. Either way, it is something to try, and it should change the owner to you.

---

### Post by oldfred on 2009-10-01
You need to make a directory, mount the partition to the directory, give rights to the directory to you- chown and edit your fstab to make mount permanent, and finally copy files.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
# see above for labeling & mounting & permissions
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by mario_ramalho on 2009-10-01
I tried several "chown" commands, but nothing happened. On the fstab tutorial, i tried different methods, but it's painfully complicated for an inexperienced user like me, so it's like reading some alien language, and the results were null. I think i may be in way over my head with this one, since i can't understand why i can't have access to my own hardware inside an operating system, and even some folders and places of the OS, like the file system. I know it's all for security, but im supposed to be the admin... I just don't get it.

Thank you for the suggestions.

Mario


  <edit>


(A few minutes later....) :P

OK, guys, the problem seems to be solved, all i had to figure out was to use the terminal under "root"... told ya i was a noob, lol. In the end, both solutions worked, so thank you guys, for the awesome help. I'm sure i'll be back with more easy questions.

Mario

---

