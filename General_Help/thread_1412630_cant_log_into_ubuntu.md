---
title: "cant log into ubuntu"
date: 2010-02-21
forum: General Help
---

### Post by mittparadox on 2010-02-21
not normaly anyway. i have win7 and ubuntu installed. i havent been in ubuntu the last few months but logged in yesterday. i got a lot of updates and restarted when they where done. but when i try to log in i get a black screen with a green line from side to side and all i can do is ctrl + alt + delete to restart. (the ubuntu logo show up first but then it blinks and i get that green line) 
i can log in if i use recovery option.
choose start up normaly from there, log in from the console there and type startx.
now im in but i cant access any of my hdd's. i just get: Can't mount "HDD Name" Not Authorized. any idea whats wrong? am i still in recovery mode somehow? or limited user or sumit. and how do i fix so i can log in normaly :D
i did try the repair options in recovery menu but it dident seems to fix anything

as you might understand i dont know to much about linux, so dont go to advanced on me :P

---

### Post by 2hot6ft2 on 2010-02-21
When grub loads and gives you a choice of what you want to boot into, do you have more than 1 kernel option?
Like 
2.6.31-17
and
2.6.31-19

If so try booting into the lower numbered kernel. i.e. the one that worked before.
By default it chooses the higher number because it's newer and the 2.6.31-19 has given several people problems.

---

### Post by mittparadox on 2010-02-21
yes i have:

2.6.31-19
2.6.31-19 Recovery Mode
 
2.6.31-16
2.6.31-16 Recovery Mode

2.6.31-14
2.6.31-14 Recovery Mode

two mem test options and win7

not entirely sure whit the numbers but something like that. 
and all options gives the same result.
all three recovery options work, the other dont.

btw, i dont seems to have sound anymore either? -_-

---

### Post by 2hot6ft2 on 2010-02-21
I haven't seen your issue before so we'll have to wait for someone more familiar with it to show up.

---

### Post by mittparadox on 2010-02-22
any ideas anyone? :confused:

---

