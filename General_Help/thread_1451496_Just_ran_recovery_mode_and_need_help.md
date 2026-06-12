---
title: "Just ran recovery mode and need help"
date: 2010-04-10
forum: General Help
---

### Post by VEI2I7AS on 2010-04-10
Hi Im new to the linux system so i havent completely figured out the command line, but i just ran recovery mode and it ran fine. I logged in. now it says

(user 1 is my username)

user1@user1-desktop:~$

How do i get back to my actual desktop?

---

### Post by darolu on 2010-04-10
Starting X should do the trick:
```
~$ startx
```

Do you get to a terminal when you start with your regular kernel as well? (no recovery mode)

---

### Post by WinterRain on 2010-04-10
startx

---

### Post by VEI2I7AS on 2010-04-10
lol Thankyou both TONS!!

---

### Post by garvinrick4 on 2010-04-10
If startx does not do the job, it should. Here is restart from terminal.


sudo shutdown -r now

---

