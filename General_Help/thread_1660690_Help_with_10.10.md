---
title: "Help with 10.10"
date: 2011-01-05
forum: General Help
---

### Post by harecanada on 2011-01-05
I installed 10.10 and did system test and everything was fine. Now when I try to run it, I get to the opening page then no joy. Can't open anything and if I click on Firefox or anything they just shut down and disappear off the screen. I need some help fast as I use this for business. Anybody willing to give me some pointers? Using Inspiron 531 ,
Thanks

---

### Post by happyhamster on 2011-01-05
Try pressing ctrl-alt-F3. This will put you into a console. Login, then run:
```

sudo apt-get update
sudo apt-get upgrade

```
If that worked, take a look if things improved:
```

sudo service gdm restart

```
Good luck.

---

### Post by harecanada on 2011-01-05
Thanks for the response. I get to the login but when I put the password in I get an error
[1333.022369] end_request: I/O error, dev sda, sector 755249864

What the heck does that mean?

---

### Post by happyhamster on 2011-01-05
That likely means the harddrive is failing. sda is usually the harddrive, but it could be the dvd drive in some configurations. If you have a dvd in the dvd-drive, see if removing it changes things.

If that doesn't help, you should run a disk check. Try booting from a live cd, and force a disk check from there:
- Boot from a live-cd.
- Open a terminal (Applications-->Accessories-->Terminal), and run:
```

sudo fsck /dev/sda1

```
Note that the harddrive must *not* be mounted when running fsck. This is the default situation when booting into a live environment, so if all you do is the above, you should be fine.

Good luck.

---

### Post by harecanada on 2011-01-05
This is what I get when I do that:

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda1: clean, 161162/29974528 files, 2766604/119881216 blocks

---

### Post by harecanada on 2011-01-05
I'm pi##$^%& off!! I had 9.04 working forever. Then I got lured into upgrading to 10.10 and now my system is completely messed and I use it for work. For the first time in 5 plus years I have resorted to loading Windows [Vista] on my system. And worst of all I took an Acer Aspire 5315 laptop which was totally screwed and loaded 10.10 on it and I can't make the thing crash!!! I'm so mad!!!!

---

### Post by ekjsim on 2011-01-05
Chill hare. Chill.... Ubuntu 10.10... I started having issue right from the beginning when I first installed it. Still having problem... The only thing we can do, is wait for 11.04.

---

### Post by harecanada on 2011-01-07
But I took a really crappy Aspire 5315 laptop that would not work and I put 10.10 on it and it works like a brand new computer. Absolutly no problems. That's what drives me crazy.

---

