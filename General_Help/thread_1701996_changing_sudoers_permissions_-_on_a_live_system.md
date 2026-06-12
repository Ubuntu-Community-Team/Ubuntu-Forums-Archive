---
title: "changing sudoers permissions - on a live system?"
date: 2011-03-07
forum: General Help
---

### Post by amoebios on 2011-03-07
Okay, guys, i have this problem and i may need professional help; it appears smb4k made my /etc/sudoers file writable (according to [log](http://pastebin.com/ZKM8dYnr)), hence, any sudo command will coerce this error: 
```
 
ubuntu@ubuntu~$ sudo any 
sudo: /etc/sudoers is mode 0640, should be 0440
sudo: no valid sudoers sources found, quitting 

```

i wanted to boot into recovery console and chmod 0440 /etc/sudoers, but it's a live system - it doesn't have a recovery mode. (more here: [http://ubuntuforums.org/showthread.php?t=1695680](http://ubuntuforums.org/showthread.php?t=1695680) ) 

How would i mount the live system from another liveCD?

---

### Post by Stephen Morgan on 2011-03-07
A live CD ought to reset everything when you restart the computer. Is it a Live USB you're using?

---

### Post by lithopsian on 2011-03-07
If you boot with a Live CD, it will automatically mount any partitions that it finds, including your Ubuntu installation on the hard drive.  Then you can change anything you like.

---

### Post by psusi on 2011-03-07
If it is a liveusb with persistent storage, then it is using the SysLinux boot loader.  You should be able to hold down shift or press tab during boot to get it to prompt you for additional kernel arguments.  Add the word "single" and that will get you to rescue mode.

---

### Post by amoebios on 2011-03-07
Thank You, appending 'single' worked! 

Then why did it say there's no "dedicated recovery mode"? Nevermind, i don't even remember how i got there....

Back to finding out how to make some room. :guitar::lolflag:

---

