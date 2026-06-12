---
title: "Ubuntu 10.10 won't start"
date: 2012-09-13
forum: General Help
---

### Post by zander x on 2012-09-13
Hello.

I was copying images to my desktop yesterday. The first folder went fine, then the second one started to have problems copying and then deleting. I figured that would be a good time to reset the computer. Some sort of HD error has occurred because now, Ubuntu won't start up.

I took a picture of the screen. Any clues on how to get around this little problem?

---

### Post by zander x on 2012-09-15
Anyone?

---

### Post by Bashing-om on 2012-09-15
zander x;

   Just saw your post ...try this to repair your file system.


1. Boot from the Ubuntu Live CD;
2. Open a Terminal;
3. in the terminal run:```
sudo fdisk -l

```(to get the device name) then press ENTER;
4..in the terminal run:```
sudo fsck /dev/sdXY
  
```  where XY replace with the results of fdisk  (ie sda1),then press ENTER;
5. Restart the system and boot normally.

---

### Post by linux_tech on 2012-09-15
From live CD, open terminal, and type in 

sudo fsck /dev/ubuntu partition

---

### Post by josephmills on 2012-09-15
10.10 is unsupported you may want to upgrade 
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

meaning you are not going to get security updates

---

### Post by zander x on 2012-09-16
Thanks for your help, guys! Now I can get back to Ubuntu, but now it's very slow loading. I suspect the hard drive is going bad.

I know 10.10 isn't supported, but I thought I had installed 10.04 when I put it on this computer. I don't like the new versions because the new Gnome and Unity are crap. I feel like I've been bullied into a choice by some megamanical company from Cupertino or Redmond.

---

### Post by Bashing-om on 2012-09-16
Good deal !
 
As the original situation is resolved, Please mark this thread as solved. 

Start new thread with the slow loading situation and we will cope with it on a case by case basis.

[INDENT]kind regards <==BDQ
[/INDENT]

---

