---
title: "Cleaning up trash"
date: 2010-11-25
forum: General Help
---

### Post by kanishkdudeja on 2010-11-25
when i write 

gksudo nautilus in the terminal and open up trash..

the following message gets displayed..i want to get rid of the items in trash..how can i do it

---

### Post by kanishkdudeja on 2010-11-25
bump

---

### Post by drs305 on 2010-11-25
Probably more than you want to know about Trash in Ubuntu (although I don't know why you are getting that message):
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by kanishkdudeja on 2010-11-25
thanks a lot..i recovered 3 gb of space by that manual..but still that error shows up when i open trash..

---

### Post by drs305 on 2010-11-25
Glad the trash is emptied now at least. 

I did some poking around looking for a solution for the error message (even found some of my old posts) but found nothing definitive.  There was an old bug report that mentioned reinstalling nautilus and gvfs and then rebooting. Several bugs mentioned gvfs but only the one suggested the fix was to reinstall those apps and it was several years old. 

```
sudo apt-get install --reinstall nautilus gvfs
```

---

### Post by kanishkdudeja on 2010-11-25
ive tried reinstalling both these packages and then rebooting..

it still doesnt work..

chuck it..it isnt much of a prob..

the error message is displayed only when i try to open trash in file manager using administrative rights..

but another problem has suddenly cropped up..

all my deb packages have suddenly disappeared..

before emptying trash, packages of total 450 mb were detected in aptoncd..

now only 60 mb is shown..

all my deb files of packages sun-java6-jdk, ubuntu-restricted-extras etc seem to have gone..not detected by aptoncd..

its not much of a problem but i want to know how they disappeared..

so that i do not commit the same mistake again in the future..

---

### Post by dino99 on 2010-11-25
have you checked /var/apt/cache/archives/

whole reconfiguration:

sudo dpkg-reconfigure -phigh -a

---

### Post by kanishkdudeja on 2010-11-25
there is no folder named apt in var directory

---

### Post by drs305 on 2010-11-25
I haven't used aptoncd but if it looks at /var/cache/apt/archives and you have run "apt-get clean" that might explain things. That command empties all the downloaded .deb packages in that folder.  Just a guess.

---

### Post by kanishkdudeja on 2010-11-25
@drs305..

omg yeah yeah..

there were some tutorials to free up space..

but i dint know that command would delete all my deb files..

nevermind..will be careful enough to not run a command blindly again..

thanks a lot..

---

