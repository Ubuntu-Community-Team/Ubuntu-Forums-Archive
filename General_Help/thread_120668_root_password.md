---
title: "root password?"
date: 2006-01-23
forum: General Help
---

### Post by nakedLefty on 2006-01-23
Hey Guys,

For christmas I was given a Radeon 9250 graphics card, and naturally I installed it first change I got.

Only problem is, apperently Ubuntu didn't like it, as I was running a Matrox card before, so during boot, it left me at a prompt unable to start "x". 

I tried to apt-get/install the Ati drivers, but it'll only let me do that as "root", and I don't know what the root password is?!?

Please help me guys, I like Ubuntu, or at least have liked it up untill this point :)

What's the pass????


/nL

---

### Post by lnxpwr on 2006-01-23
try:    sudo apt-get install <whatever_you_need>
the asked password is your userpassword !

---

### Post by nakedLefty on 2006-01-23
[QUOTE=lnxpwr]try:    sudo apt-get install <whatever_you_need>
the asked password is your userpassword ![/QUOTE]

Okay, I'll give that a shot... as the "regular" apt-get gave me the "you need to be root to do this..." type of message.

I'll be back if it gives me more lip :)

/nL

---

### Post by nakedLefty on 2006-01-23
hmmm... now I guess I have the drivers install... now I just need to let "x" know what to use for it's "screens"?!?

Does Ubuntu come with a "some what" graphical x-config setup that will allow me to change it's setting from the old matrox card to the new ati card, with out too much trouble?

thanks in advance.

/nL

---

### Post by rjwood on 2006-01-23
```
sudo dpkg-reconfigure xserver-xorg
``` go through the process and let X detect your hardware unless you know what you are doing. Good Luck!!!

---

### Post by lnxpwr on 2006-01-23
give this a try:    sudo dpkg-reconfigure xserver-xorg
geetinx
p.

---

### Post by nakedLefty on 2006-01-23
Hey guys, just wanted to thank you for the  solution :) it seems to work now :)

And The nL is a happy go lucky-"linux-geek" again :)


Thanks a bunch,
/nL

---

