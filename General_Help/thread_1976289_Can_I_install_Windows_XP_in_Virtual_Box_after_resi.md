---
title: "Can I install Windows XP in Virtual Box after resizing the root.disk to 35 GB ?"
date: 2012-05-08
forum: General Help
---

### Post by curiousapprentice on 2012-05-08
I have read on this :[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)  article that it is possible to increate the hdd space I currently have.

Im running out of space. I have only 2 GB left. 

1. If I increase the hdd space using that method do I loose any application I currently have ? 
2. Is there any risk of overwriting Windows files ?
3. What is swap.disk ? Do I eed to increase the swap disk too ?
4. I want to run Windows Xp in Viirtual box. Can I do that after I increase the root.disk ?
5. After increasing root.disk if everything works fine why do I need to keep oldroot.disk ?

6. Does increasing the root.disk increases the probability of file system corruption due to hard boot ?
7. Do I currently have less chance of file corruption ?

8. How much time it might take to Increase the root.disk (Currently acquired 18 GB. I want to add 17 GB more  (Total of 35 GB ).
9.  What will be the command to do that ?

10.  Can I do all things after doing this increase, like playing videos,muzic, software programming, playing games etc ?


Is there any precautions I need to take ? What will be the disadvantage of this increase ?

---

### Post by Mark Phelps on 2012-05-08
> **curiousapprentice said:**
> 1. If I increase the hdd space using that method do I loose any application I currently have ? 
First things first -- terms. You're increasing the size of the virtual file used for Ubuntu, NOT the size of the hard drive.

Second, if the root.disk file is in the same partition that has only 2GB of free space left, and this is the OS partition for Windows (as opposed to a separate data partition), then you are out of space already.  MS Windows needs some free space to load and run.  If you expand the root.disk file to take up that space, Windows will no longer work.
> 2. Is there any risk of overwriting Windows files ?
No -- free space is just that, it has no files allocated to it.
> 3. What is swap.disk ? Do I need to increase the swap disk too ?If that is already the proper size, increasing it will do you no good.
> 4. I want to run Windows Xp in Viirtual box. Can I do that after I increase the root.disk ?
IF you're talking about installing XP inside VB inside Wubi -- I don't think that is even possible; even so, since Wubi is already installed inside a virtual file system (in effect), why would you even want to do that?
> 5. After increasing root.disk if everything works fine why do I need to keep oldroot.disk ?Sorry, don't know.

> 6. Does increasing the root.disk increases the probability of file system corruption due to hard boot ?NO
> 7. Do I currently have less chance of file corruption ?NO

> 8. How much time it might take to Increase the root.disk (Currently acquired 18 GB. I want to add 17 GB more  (Total of 35 GB ).Probably about the same amount of time that it took the first time -- but, really don't know.
> 9.  What will be the command to do that ?The commands are already provided in the link you cited.

Seriously, if you're running out of room in Ubuntu because you've grown to using it a LOT, now is the time to move away from Wubi into a separate install -- where these size and other problems are more easily addressed.

> 10.  Can I do all things after doing this increase, like playing videos,muzic, software programming, playing games etc ? None of those things are specifically related to the SIZE of the Wubi file.  IF these things aren't working for you, there are problems other than the size of the root.disk file.


> Is there any precautions I need to take ? What will be the disadvantage of this increase ?Those are already mentioned in the linked article. Messing around with filesystem sizes always carries some risk of filesystem damage.  IF there is stuff you can not afford to lose, you should back it off to external drive(s) before you attempt this change.

---

### Post by curiousapprentice on 2012-05-08
[COLOR=Red]**1.** [/COLOR]I have total 135 GB  space in C:/ (sda1) out of which I still have 50 GB Free. My total HDD size is 500 GB.

[COLOR=Red]**4. **[/COLOR] Actually my main aim is to test several other linux based OS (CentOS,Gentoo,BSD etc) under VB. I have some programs which can not run on Win 7 x 64 which is my primary OS, so I need Win XP.

[COLOR=Red]**9**.[/COLOR] How I can move to a separate partition without loosing all my programs and customizations ? Is it even possible ?

[SIZE=1][COLOR=Red]**10.**[/COLOR][/SIZE] Everything is working file. I asked that out of Curiosity.

---

### Post by oldfred on 2012-05-08
I think there is a maximum size that wubi can be.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Even the creator of wubi thinks after you have used it a while you will move to a full partitioned install.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

