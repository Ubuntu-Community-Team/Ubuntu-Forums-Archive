---
title: "boot problem"
date: 2009-08-10
forum: General Help
---

### Post by yetiking on 2009-08-10
i downloaded ubuntu over windows 7 and used unbuntu to creat 2 equal partitions. then after 3 or so months i loaded the new version of windows 7 over the existing 7 partition. problem is, now its not allowing me to chose between partitions, however i know my linex partition is there.

if theres anyway i can boot into it with out wiping it clean that would be great.

thanks for the help
Daniel

---

### Post by merlinus on 2009-08-10
Whilst running from a live cd, open a terminal and enter these commands, one at a time:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use hd and numbers from the previous command
setup (hd0)  #use hd and its number from the previous command
quit 
```

Remove the cd and restart.

---

### Post by yetiking on 2009-08-10
you guys are gods.....

i don't understand at all how that worked but it did, thanks a ton


i have 3 other problems i need some help on if you don't mind-

# 1- i cant get ubuntu to keep my resolution settings: when i boot up i'm always at 4:3 when my screen is a 16:9. i have the apropriate graphics software... i think....

 the next to are petty things-

1- i cant adjust the sensitivity on my mouse low enough.

2- i cant find a fan speed control software that works- i have a really loud cpu fan.


thanks merlinus i cant tell you how much i apriciate the help

Daniel

---

### Post by merlinus on 2009-08-10
Glad it is working.

Did you try System/Preferences/Display to set up your monitor?

Cannot assist on the other two issues.  Perhaps googling for your mouse will bring some useful info.

---

