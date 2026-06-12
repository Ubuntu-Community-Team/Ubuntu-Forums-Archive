---
title: "Clone or duplicate a user"
date: 2009-11-15
forum: General Help
---

### Post by rslaqui on 2009-11-15
Hi I'm a newbie installing a system that will have two kind of users:

eng. students and social sciences students. As you may figure the apps menus and setting of one group will differ those of the other.

I don't want to change every user&#347; menu and settings manualy so I thought I could have a couple (one for each kind) of Base (Model) users and clone their settings every time a new user is added.
------------------------------
 I found [http://ubuntuforums.org/showthread.php?t=365440](http://ubuntuforums.org/showthread.php?t=365440)

which tells to do:
sudo adduser newEng
sudo cp -R /home/EngModel/* /home/newEng/
sudo chown -R newEng:newEng /home/newEng
------------------------------------------------------

I made a simple test.
-> creating EngModel
-> login in as EngModel
-> changing EngModel's background

-> login out -> login as my admin user (the sudo capable)

typing: (with the proper identification and password setting)
sudo adduser newEng
sudo cp -R /home/EngModel/* /home/newEng/
sudo chown -R newEng:newEng /home/newEng

and 

-> login out -> login as newEng

and the background was the default ubuntu 9.10 x64 bkg NOT the one setted in EngModel :-(


----------

Any ideas to solve my problem?
or where I did wrong the cloning?


thanks a lot.
RSL

---

### Post by lloyd_b on 2009-11-15
Your problem is that "sudo cp -R /home/EngModel/* /home/newEng/" will NOT copy files/directories that start with a period, which is where most of the per-user configuration is stored.

Try running this in addition to your original commands (before the 'chown' command):```
sudo find /home/EngModel -name ".*" -exec cp {} /home/newEng \;
```This will locate all the files/directories starting with ".", and copy them as well.

(Note: you can NOT just do "cp -R /home/EngModel/.* /home/newEng" because of the existence of the ".." entry, which specifies the parent directory.  'find' avoids this issue).

Lloyd B.

---

### Post by rslaqui on 2009-11-16
Wow thanks a lot:

Just to small fix to your post

find /home/EngModel/ -name ".*" -exec cp **-R** {} /home/newEng/ \;

the -R is needed because otherwise all the .directories are omitted by cp.
------
And for the ADMINS I tried to add a post in [http://ubuntuforums.org/showthread.php?t=365440](http://ubuntuforums.org/showthread.php?t=365440) to complement it and/or redirect to this thread but since it's tagged as resolved I can't do it.

thanks ;-)

---

### Post by Bag-O-Stuff on 2009-11-16
This is easier and gets all the dot files and directories:

cp -a /home/EngModel /home/newEng

---

