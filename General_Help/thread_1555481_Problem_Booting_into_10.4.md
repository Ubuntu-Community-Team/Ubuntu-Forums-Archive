---
title: "Problem Booting into 10.4"
date: 2010-08-18
forum: General Help
---

### Post by CapitalDave on 2010-08-18
I've been away from home for a while, so I got home and updated my Ubuntu with all the latest updates. I seem to be having some problems with my graphics since the update.

When I boot up, on the Esc boot menu, I can boot into 
1) kernel 2.6.32-24
2) kernel 2.6.32-22
3) kernel 2.6.31-19
or 4) kernel 2.6.28-16

Booting into these different modes causes different problems, 2.6.32-24 boots to a blank (apart from a white cursor at the top of the screen, but no input is accepted) black screen.
Booting to option 2 causes the same problems. Booting to option 3 seems to boot just fine (that's what I'm using just now) and booting to option 4 reaches the log in screen, but is then followed by a black screen displaying the message 'Cannot display video in this mode'

I'm assuming that this is something to do with a new update's incompatibility with my graphics card, I've seen other such problems on various forums, but none of the solutions worked, and none of the descriptions seemed to describe my specific predicament.

Any help/advice would be greatly appreciated, sorry if this has already been solved elsewhere (I did a search but didn't find anything), if it has a point in that directly would also be appreciated.

---

### Post by Rubi1200 on 2010-08-18
Hi and welcome to the forums :-)

It is quite likely a graphics issue, but we need to know what card you have.

The next time you boot into the kernel that works, go to Applications > Accessories > Terminal and post the output of this:

```
lspci | grep VGA
```

Once we know what card you have, offering a solution should be easier.

Thanks.

---

### Post by CapitalDave on 2010-08-18
Thanks for your help

This is the output from terminal

```

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

Thanks again,

---

### Post by Rubi1200 on 2010-08-18
> **CapitalDave said:**
> Thanks for your help

This is the output from terminal

```

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```Thanks again,
Thanks for the output.

Take a look here and see if your card is mentioned or any other workaround that may help:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

If not, you may have to stick with the kernel you are on until the next update/upgrade which may or may not fix your situation.

---

### Post by wynand2020 on 2010-08-18
Install Windows

---

