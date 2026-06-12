---
title: "Urgent! Messed up my Ubuntu bad with chown and chmod!"
date: 2009-09-26
forum: General Help
---

### Post by mac666 on 2009-09-26
Hey
I was trying to get rid of an error msg i get everytime i boot, that the users .dmrc file does not have the correct permissions...
how ever i changed it each time i booted and i got angry with it, so i tried to change the hole /home/user catalog to 644 rights and that i owned it...

But now i cant access my home folder :P

If i try to run:
**sudo chmod -R 644 /home/user**

I get Access denied for each and every folder/file under it...

If i try to run:
**sudo chown -R mac /home/mac/**
i get access denied for /home/mac/.gvfs

I dont dare to reboot, fearing what can happen...
Please! help!

---

### Post by mac666 on 2009-09-26
Ok i fixed it partly with 
**sudo chmod -R 777 /home/mac/**


But what SHOULD it be? :|

---

### Post by sideaway on 2009-09-26
Haha, playing around with permissions and home folder huh? I've done exactly what you've done a number of times :P The permissions for the home folder should be 644, however you need to make sure you're the owner.

---

### Post by sideaway on 2009-09-26
Sorry forgot to give you these: :lol:

chown -R username:username /home/username
chmod 644 /home/username/.dmrc
chmod 644 /home/username/.ICEauthority

---

### Post by mac666 on 2009-09-26
But how to give my home folder 644?
Each time i try i really mess it up :D!

---

### Post by the_squircle on 2009-09-26
> **mac666 said:**
> But how to give my home folder 644?
Each time i try i really mess it up :D!

```
chmod -vR 644 /home/mac666
```

---

### Post by bodhi.zazen on 2009-09-26
If it is just home you can recover easily.

boot to recovery mode

mv /home/mac666 /home/mac666.old
mkdir /home/mac666
chown mac666:mac666 /home/mac666
chmod 770 /home/mac66

Then reboot or continue the boot process.

You can then move any data you need from /home/mac666.old

This is why I make a separate /data partition and keep only config files in /home.

---

### Post by mac666 on 2009-09-29
First reboot in a while, my .dmrc file is still messed up, or my /home folder...

Each time i try to do something, it wont work... what exactly do i need to do?
my .dmrc file has 644 and i OWN it...

What more does it want?!

---

### Post by bodhi.zazen on 2009-09-29
> **mac666 said:**
> First reboot in a while, my .dmrc file is still messed up, or my /home folder...

Each time i try to do something, it wont work... what exactly do i need to do?
my .dmrc file has 644 and i OWN it...

What more does it want?!

Did you try my method ?

See also : [http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

---

