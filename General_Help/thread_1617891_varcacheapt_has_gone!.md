---
title: "/var/cache/apt has gone!"
date: 2010-11-09
forum: General Help
---

### Post by trbone on 2010-11-09
Please help!

I was following some instructions to move my  /var/cache/apt folder to a RAM drive, when the instructions generated an error message (I can't remember the exact message). The instructions were as follows.

sudo mv /var/cache/apt /media/HOME/
sudo ln -s /media/HOME/cache /var/apt/

Following this I tried to undo whatever I had done following the instructions to undo the change as follows.

sudo rm /var/cache/apt
sudo mv /media/HOME/cache /var/apt/

This also generated error messages, along the lines of "mv: cannot stat `/var/cache/apt': No such file or directory"

Now when I look for the folder it appears to have vanished. I was wondering if any of you can help me to get it back. It seems to be important...

I am running Eeebuntu standard version 3. My machine is a Eeepc901. If there is any other information I can give you then let me know...

Thanks :)

---

### Post by trbone on 2010-11-11
I should add that in the above instructions I replaced the "/media/HOME/" with "/dev/shm/"

Don't know if this makes any difference...

---

### Post by dcstar on 2010-11-11
> **trbone said:**
> Please help!

I was following some instructions to move my  /var/cache/apt folder to a RAM drive, when the instructions generated an error message (I can't remember the exact message). The instructions were as follows.
........

Firstly, that is an exceptionally stupid thing to do as that system folder is temp storage for any packages that are downloaded, and having it in a finite-sized RAM drive makes no sense at all and could cause all sorts of problems.

You cannot just play around with system folders that have specific requirements and are located where they are now for very good reasons.

Secondly, try this and see if Synaptic works correctly:

```
sudo mkdir /var/apt/cache
```

---

### Post by trbone on 2010-11-14
> **dcstar said:**
> Firstly, that is an exceptionally stupid thing to do as that system folder is temp storage for any packages that are downloaded, and having it in a finite-sized RAM drive makes no sense at all and could cause all sorts of problems.

You cannot just play around with system folders that have specific requirements and are located where they are now for very good reasons.

Secondly, try this and see if Synaptic works correctly:

```
sudo mkdir /var/apt/cache
```

Thanks dcstar. That worked once I had created a /var/cache/apt/archives/partial as well.

As for the stupidity of my actions.. you may well be correct, but I was just following the advice from [this thread]("http://forum.eeebuntu.org/viewtopic.php?f=42&t=4433&sid=7bbddb6d5ad7194ac5c495aacca3651b") on the seventh post.

Your main concern about the RAM drive being finite sized isn't valid because the drive that /var/apt/cache is normally on is only 4GB and it has far less then the 1GB of free space that my RAM drive has. In fact the reason that I wanted to move the /var/apt/cache was to free up space on my primary partition...

If anyone else has some good ways of clearing up space on my primary partition I am all ears. I have already moved my /home folder to a seperate drive...

TrBone

---

### Post by drs305 on 2010-11-14
> **trbone said:**
> 
If anyone else has some good ways of clearing up space on my primary partition I am all ears. I have already moved my /home folder to a seperate drive...

TrBone

Take a look at this thread:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

It provides various ways to find out what is taking up space if you think you should have more free space available than you do.

---

