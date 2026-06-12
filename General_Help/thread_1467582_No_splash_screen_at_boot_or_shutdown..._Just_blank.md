---
title: "No splash screen at boot or shutdown... Just blankness."
date: 2010-04-30
forum: General Help
---

### Post by fraseyboy on 2010-04-30
Since upgrading to 10.04, there is no longer anything happening at startup or shutdown. For the 30 seconds between GRUB and my Ubuntu desktop there is just a black screen. Everything works fine after that. It's the same thing for shutting down.

Any idea's?

---

### Post by ninja togo on 2010-04-30
It's the same with mine, except for the shutdown, that's the only time that I see it for maybe 1 or 2 seconds.

---

### Post by shungun on 2010-04-30
Yes same for me too, While booting there is no splash, (it worked for 9.10) and there is a splash for just around 2 seconds while shutting down.

---

### Post by ninja togo on 2010-04-30
If anything it's a way that Ubuntu 10.04 shaves off those seconds from the boot time. If that's the case then I will settle, however I still want my main menu, "system" icons back and those from the firefox context menu.

---

### Post by fraseyboy on 2010-05-01
10.04 actually boots slower for me so there's really no benefit to not having a splash screen.

---

### Post by shungun on 2010-05-01
Nope, its not a way to shave time off, I tried a liveCD and i saw a splash screen! its only after i installed it...

---

### Post by dbloom on 2010-05-01
same here.  just did a clean install of 9.10 about a week ago, too. and it does seem to take longer on boot.  i never see grub, it just goes from POST to black to gdm.

System Specs:
AMD Phenom II 965 (3.4GHz)
8GB Ram
2x 9800 GTX+ (SLI)
64-bit ubuntu (separate /home partition)
(i think that covers the important bits)

---

### Post by pazuzuthewise on 2010-05-01
There is a splash screen, it's just that it uses a new and improved engine, called plymouth,  that it's so improved that we don't get to see it (or plagued by weird artifacts after installing the fglrx driver).

---

### Post by fraseyboy on 2010-05-01
> **pazuzuthewise said:**
> There is a splash screen, it's just that it uses a new and improved engine, called plymouth,  that it's so improved that we don't get to see it (or plagued by weird artifacts after installing the fglrx driver).

Doesn't seem like much of an improvement then...

Is there a way to remove Plymouth and go back to the way previous versions handled it?

---

### Post by Speed Of Light on 2010-05-01
same for me 
how can I fix this ?!

(seems like I made a duplicate thread [here]("http://ubuntuforums.org/showthread.php?p=9214085"))

---

### Post by shungun on 2010-05-03
I found a way!:o
```
sudo su
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
exit

```

This worked for me, i obtained the workaround from the following blog :
[http://goo.gl/cELb](http://goo.gl/cELb)

---

### Post by dbloom on 2010-05-03
this fixed it for me.  

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

though part of it includes shungun's solution above.  i now wonder if that's all i needed.  at any rate, its working and boots as fast as karmic so i'm satisfied.  also get all my TTY's, which is handy.

---

### Post by leandromartinez98 on 2010-05-08
shungun fix worked for me as well. Thanks.

---

