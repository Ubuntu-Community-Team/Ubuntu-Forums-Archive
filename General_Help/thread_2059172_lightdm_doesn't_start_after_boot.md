---
title: "lightdm doesn't start after boot"
date: 2012-09-17
forum: General Help
---

### Post by ebu on 2012-09-17
Hi.
Here is my problem. Once upon a time after another update my wife's note didn't come up after reboot. There was just black screen. I can't remember what was written in the logs, but after brief googling I got lightdm replaced with gdm. It worked, my wife was able to login again. But later it appeared that with gdm the notebook can't be locked, or rather after being locked it can't be unlocked. Only reboot brings it back to life. It's not good as we should lock it frequently to not get occupied by kids. So I tried to install lightdm back. With lightdm it can be perfectly locked and unlocked, but there is still black screen after reboot unless I manually launch it from root shell. Unfortunately my wife doesn't like to run her note this way and threatens to install windows if I don't fix it. 

So, the question, why that beloved lightdm do not want to run automatically? /var/log zip as it is after reboot is attached.

Best regards, Eugene.

---

### Post by jerrrys on 2012-09-18
try this

sudo dpkg-reconfigure lightdm

---

### Post by newb85 on 2012-09-18
> **jerrrys said:**
> try this

sudo dpkg-reconfigure lightdm

+1

---

### Post by ebu on 2012-09-19
reconfigure didn't help, had to manually fix it as described in here [http://ubuntuforums.org/showthread.php?t=2049203](http://ubuntuforums.org/showthread.php?t=2049203).

---

### Post by jerrrys on 2012-09-19
congratulations :)

 [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

