---
title: "i can't replace 11.04 with 10.04 from a boot cd"
date: 2011-09-22
forum: General Help
---

### Post by Goat Engine on 2011-09-22
Ok so here's the story: I bought a laptop, and replaced the pre-installed windows with ubuntu 11.04. Didn't like 11.04, the sound was messed up, and it kept freezing after I logged in. So I decided to try and revert to 10.04.

I made a 10.04 boot CD, changed the settings so that my computer would boot from the CD, except when I start the computer with the CD in place, it just goes straight onto 11.04 as if the CD isn't there.

The crashing seems to have stopped now, so on my desktop you can see the Ubuntu boot CD. Why can't I boot from my CD?

---

### Post by Rubi1200 on 2011-09-22
Hi and welcome to the forums :-)

I would start by checking the integrity:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also try burning at the lowest possible speed for best results.

If your laptop allows it, try creating a bootable USB and give that a try.

I recommend UNetbootin for the job:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by SpatryX on 2011-09-22
I would also like to recommend that you check to make sure BIOS is configured to boot from CD before it looks at your hard drive. Depending on your computer model, you will need to press Esc, F1 or some other key to access it.

---

