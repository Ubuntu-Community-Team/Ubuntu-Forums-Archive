---
title: "Problem booting with ati graphics card"
date: 2009-07-30
forum: General Help
---

### Post by CameronJohnson on 2009-07-30
Hey, sorry if this has been answered already but I have some trouble after installing Ubuntu 9 on my Inspiron e1505 dual booting Ubuntu and Vista. 

After I select Ubuntu in Grub the computer boots normally and makes it to the Ubuntu logo and loading bar, but directly after that it shows some random green and red lines at the top of the screen and hangs. I have an ati mobility radeon x1400 graphics card, which I think may be the problem. 

I have successfully used this computer to boot Ubuntu 8, and was able to boot Ubuntu 9 until this sudden failure. 

Any help would be greatly appreciated.

---

### Post by TeoBigusGeekus on 2009-07-31
Older ATI cards are no longer supported by the company for linux.
Opensource drivers are not yet developed adequately enough to make these cards work.
I'd go with 8.10.

---

### Post by bluelamp999 on 2009-07-31
I'm in a similar place (marooned in Intrepid land)...

Any word on how the development of the open source ATI drivers is coming along?

---

### Post by Mars73 on 2009-07-31
Weird, I have a HP 6820s notebook with an ATI X1350 and have no problems whatsoever with the opensource drivers. Compiz, wobbly windows and cubes all work fine. When installing 9.04 I got the warning that my videocard was not supported by Ati (or something like that) but could use the opensource drivers, I continued and am very pleased with it. I don't notice any difference with older ubuntu versions (thanks to whoever made the opensource drivers).
Maybe try with a live CD and see how it goes?

---

### Post by CameronJohnson on 2009-07-31
Well the thing is I was able to boot up properly a couple of times before it crashed. Is there anyway I can by-pass the ati card and only use software rendering? If not I'll probably just downgrade. Thanks a lot for all the help.

---

### Post by TeoBigusGeekus on 2009-07-31
Had exactly the same problems with a Radeon 1950Pro. It booted a couple of times normally, then booted whenever it wanted and then once every 20 times. Thank god the cpu on that pc was burnt by a power failure and I was able to replace it with a nvidia one.

---

