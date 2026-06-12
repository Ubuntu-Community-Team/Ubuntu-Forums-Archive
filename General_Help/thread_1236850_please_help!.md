---
title: "please help!"
date: 2009-08-10
forum: General Help
---

### Post by allzzzzz on 2009-08-10
I have a tc2502 running that g-os powered by ubuntu 7.10  and e17.... now heres whats up, first i cant update it when it goes to finish it says like  dependency is unsatisfiable libcairo2   next i cant update the flash player. Finally is there some sort of update download like, a major one i should do? Or should i keep it the same?

---

### Post by bodyharvester on 2009-08-10
> **allzzzzz said:**
> i cant update the flash player. Finally is there some sort of update download like, a major one i should do? Or should i keep it the same?

hi,

flash will be IN the updates, if you dont have the latest version of something it will be in the auto updates.

what do you mean by major update? do you mean the newer versions of ubuntu like 8.04 and so on?

---

### Post by frt975 on 2009-08-10
```
sudo apt-get libcairo2
``` and reupdate 
Use a descriptive titles. Not many people can help when every title is > plz help

---

### Post by allzzzzz on 2009-08-10
yea i mean like 8.04 would that be "ill-advised?''   oh and i cannot update anything it always gives an error, there are like 100 updates avail and i only picked the 3 Firefox ones and that still didn't work

---

### Post by bodyharvester on 2009-08-10
> **allzzzzz said:**
> yea i mean like 8.04 would that be "ill-advised?''

ill-advised? nope.

the two most common i see are 9.04 and 8.04, or maybe its 8.10 not 8.04:confused:

a major update isnt a bad thing, 9.04 has poor drivers for integrated chipsets in comparison the the previous one which i think was 8.10

---

### Post by allzzzzz on 2009-08-10
im quite green when it comes to linux ill be able to find some tutorial or something to upgrade to the 8.04 or 8.01?

---

### Post by bodyharvester on 2009-08-10
> **allzzzzz said:**
> im quite green when it comes to linux ill be able to find some tutorial or something to upgrade to the 8.04 or 8.01?

as far as im aware the update manager updates your system by itself so long as its been set to, see the pic.

it should show the upgrade to the next version in the list, you have to upgrade through each version, not just straight to 9.04

---

### Post by michy99 on 2009-08-10
The version you are running, Gutsy Gibbon, is no longer supported. You need to change the repositories in your sources.list file to point at [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com). If you want help doing this, open a terminal and enter this command, then post the result here.```
cat /etc/apt/sources.list
```

---

### Post by snowpine on 2009-08-10
Gutsy Gibbon 7.10 has reached its "end of life" and is no longer supported. I strongly recommend backing up your documents and doing a fresh install of the current version, 9.04 Jaunty Jackalope.

---

### Post by allzzzzz on 2009-08-12
[FONT=monospace]i put in the command but i cant figure out how to copy and paste the result... this makes me feel stupid cus i know its gonna be real simple

[/FONT]

---

### Post by allzzzzz on 2009-08-12
ok all i basically want to achieve is update my flash can someone really help me cus ive had alot of ppl try to no avail....

---

