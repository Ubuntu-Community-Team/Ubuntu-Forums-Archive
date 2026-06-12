---
title: "BackinTime, permission problems, 2nd Internal HD"
date: 2011-05-31
forum: General Help
---

### Post by fisheater on 2011-05-31
Problem: permissions for rsync and BackinTime.

Setup: Ubuntu 11.04, Two internal HD, #1=main, single boot, #2=backup drive.

Question: How do I set up my 2nd HD with correct permissions?

Background: I had previously a dual boot XP+10.04 with a 2nd HD formatted as NTFS. With this I was able to use my rsync and backintime to my 2nd HD with no issue. My new set up is EXT4 on both HD.

(I even tried to reformat my 2nd HD as NTFS, but that didnt fix the issue)

I followed [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) to mount the 2nd HD and get permissions. But now when I run backintime i get this error:

[E] Error: rsync: opendir "/home/myhome/.ssh" failed: Permission denied (13)

I did my requisite reading for a newbie, and am stuck. I ran backintime as root, and it backed up ok. How do I run my user version of backintime? (i.e. How do I fix the permission issue?)

Thanks!

FE

---

### Post by fisheater on 2011-05-31
Update: things that havent work to date...

sudo chown -R USERNAME:USERNAME /media/2ndHD

chmod 777 /media/2ndHD

Thanks for checking (eager to back up my stuff!)

FE

---

### Post by tredegar on 2011-05-31
Looks like permissions...

Please post the output (when you are logged in as yourself) of```
cd ; ls -al | grep .ssh
```
Please do not edit or otherwise amend the result. The security implications of this are very, very, very low [Eg: There's a user called **fish**, err, somewhere).

---

### Post by fisheater on 2011-05-31
Thanks for taking the time to review this question:

**removed**

---

### Post by fisheater on 2011-06-01
Work around #1 - saved to USB HD for the moment, data is backed up. 

Thanks for looking.

FE

---

### Post by fisheater on 2011-06-01
Update: it looked like my workaround was working, but when I woke up this AM - I received the same ssh error message when backing up to my USB HD via backintime. I'll try grsync now and see if that works...

---

### Post by fisheater on 2011-06-01
Update:

I excluded .ssh from my backintime sync and it worked. All my files are backed up except for that .ssh folder. Not sure what the consequences of this change will be, but got it done for the moment.

Suggestions?

---

### Post by tredegar on 2011-06-03
**~/.ssh** should have permissions of **700** (That's why I asked you to post the output of the code in post #3.)

Therefore only yourself, or root should be able read that directory.

If you do not back up this directory, you may lose your public / private keys. This may not be important to you, or it might be very important to you.

---

### Post by fisheater on 2011-06-12
Interesting. I think this is the issue, as I have not yet choen 700 /home yet. I was between encrypting it vs 700 it. When I get a chance I'll change that and get back to this post. Thanks again for your help.

---

### Post by fisheater on 2011-06-16
Ok, here's the output for 

```
 cd ; ls -al | grep .ssh:
```

```
drwx------  2 stonemason stonemason     4096 2011-05-25 22:27 .ssh
```

I did start another thread about chown vs chmod in Installation & Upgrades (
[http://ubuntuforums.org/showthread.php?p=10948431#post10948431](http://ubuntuforums.org/showthread.php?p=10948431#post10948431)), and now see how they now overlap. Are these threads able to be combined?

Now I understand the permissions issue a bit better - owning vs modifying a file. So from this, I hope I can work this out a bit better. At least now I understand what questions to be asking.

That said, I had mixed results.

This worked:
sudo chown -R fisheater:fisheater ./*

But this didn't:
sudo chmod -R 700 /home/fisheater

It generated this error
chmod: cannot access `/home/fisheater/.gvfs': Permission denied

I will follow the other thread for how to workout my 700 issue, and this one for your insight into the output from 
```
 cd ; ls -al | grep .ssh:
```

Thanks for taking a look at this again!

---

