---
title: "drive not mounting - problem during upgrade"
date: 2009-10-22
forum: General Help
---

### Post by diggedy on 2009-10-22
I decided to try 9.10 today but during the upgrade it asked me for my password but for some reason my mouse and keyboard would not respond, im assuming its becaue I use a bluetooth keyboard and mouse. 
The only thing I could do was reset my machine, which during an upgrade is never a good idea but I had no choice.
 
Now when im booting I get the splash screen but afterwards it says 
 
one or more of the mounts listed in /etc/fstab cannot yet be mounted (esc for recovery shell)
 
/: waiting for /dev/disk/by-uuid/730271ec-doc3-4e7a-82c5-57c74690dc19
/tmp: waiting for (null)
swap : waiting for uuid = a923825d-bf2a-4eeb-blc2-a8d41828f561
 
Can anyone help me out here? All of my stuff is backed up so if I lose the installation and have to start from scratch im fine with that, but thats more of a typical windoze fix and id like to try and fix this one.

---

### Post by diggedy on 2009-10-22
bump anyone?

---

### Post by wallmalker1 on 2009-10-25
Mine's doing the same thing & I haven't tried much yet, but this thread has a few suggestions - 

[http://ubuntuforums.org/showthread.php?p=8151569](http://ubuntuforums.org/showthread.php?p=8151569)

---

### Post by ranch hand on 2009-10-25
Well, at least you know that you shouldn't change you box during an upgrade.

Can you get to recovery?

If so can you get to the terminal with networking option?

If so run
```

sudo dpkg --configure -a

```
then
```

sudo apt-get update

```
and
[code]
sudo apt-get upgrade
[code]
when that is done try the Return to normal boot option.

See what happens.

---

