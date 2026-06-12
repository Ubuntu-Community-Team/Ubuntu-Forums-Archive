---
title: "Can't backup and restore /"
date: 2011-11-20
forum: General Help
---

### Post by atey1 on 2011-11-20
I tried using the method described here [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)  to backup a linux install on one hard drive and restore  it to another hard drive. However, when I restored and tried to login, I  get errors lik e"could not update ICEAuthority in var/lib/gdm" and "The  disk drive with UUID="..." is not ready yet or not present."

It gets to the login screen, but there are no users and it won't shut  down or restart (it clicks but doesn't do anything). I can drop to a  terminal and see all my files, but can't login.

I tried changing the drive information in /etc/fstab, but that  didn't work, it just went straight to the login screen I mentioned. 

I'm thinking this has to do with the fact that in my old drive root was  on sda3 and swap was on sda5, while on this drive, the root should be at  sda1 (the old drive was a triple booted mac/win/linux). 

Any ideas?

---

### Post by quadproc on 2011-11-20
My experience has been that .ICEauthority problems are usually due to permission problems on that file.  I would suggest changing its permissions to 644.  But it sounds like you have additional problems as well. Did you set up an appropriate master/slave drive jumper on your new drive?

quadproc

---

### Post by atey1 on 2011-11-20
I've tried changing the permissions of ICE and it didn't work. It sort of just skips the .ICEAuthority error message and goes back to that login screen with no users issue. 

I'm not sure what you  mean by master/slave jumper though. I assume that means I didn't...

---

### Post by quadproc on 2011-11-21
> **atey1 said:**
> 
I'm not sure what you  mean by master/slave jumper though. I assume that means I didn't...
Some older disk drives needed the master/slave to be either set or reset depending on how a system was set up.  The master/slave setting was usually controlled by a tiny jumper plug on the drive, near the data cable.

Newer drives usually don't have or need such a jumper.

You might be having more than one problem.  I have occasionally run into that situation and it can be difficult to figure out.  Good luck.

quadproc

---

