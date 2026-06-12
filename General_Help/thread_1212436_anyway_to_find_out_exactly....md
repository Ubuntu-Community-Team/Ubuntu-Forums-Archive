---
title: "anyway to find out exactly..."
date: 2009-07-13
forum: General Help
---

### Post by Darkoblivion2 on 2009-07-13
the reason i ask, is because im not sure if i have the latest driver for my nvidia geforce gtx 260...

i dont have any glitches or anything... i am a gamer and want everything to be at it's max potential...

thanx in advance!

---

### Post by zerhacke on 2009-07-13
copy and paste this to a terminal:

```
lspci | grep VGA
```

---

### Post by t4thfavor on 2009-07-13
It should tell you if you run the nvidia control panel from the terminal.

Another way is to look at the restricted drivers manager. I think the latest thats in the repos is 180.

You can always d/l it from Nvidia, and install the latest, but it does have the potential to break things since Conanocal has not tested it yet.

Good luck!

---

