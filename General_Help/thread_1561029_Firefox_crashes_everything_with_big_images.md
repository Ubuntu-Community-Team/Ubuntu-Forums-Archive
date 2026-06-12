---
title: "Firefox crashes everything with big images?"
date: 2010-08-25
forum: General Help
---

### Post by leoh on 2010-08-25
I am running Ubuntu 10.04, up to date, 32 bits.
I tried to open a huge (10.000 x 1.200 pixels approx) Wikipedia image, and everything crashed. Nor Firefox, Gnome or anything else responded from there. Not even ctrl+alt+del, ctrl+alt+backspace, alt+F2, etc.
Only the mouse moves, but rather slowly.

This is the image:

[http://upload.wikimedia.org/wikipedia/commons/4/4e/Itaipu_D%C3%A9cembre_2007_-_Vue_G%C3%A9n%C3%A9rale.jpg](http://upload.wikimedia.org/wikipedia/commons/4/4e/Itaipu_D%C3%A9cembre_2007_-_Vue_G%C3%A9n%C3%A9rale.jpg)

Can you confirm if the same happens to you?

I could NOT replicate the problem with Chromium. However, I am not sure if the issue is only firefox since it locks up everything in ubuntu.

---

### Post by wojox on 2010-08-25
I confirm the exact same thing happened.

---

### Post by leoh on 2010-08-25
How can I tell if this is a Firefox or Ubuntu (gnome, etc) issue?
How can we fix this?

---

### Post by wojox on 2010-08-25
If you can't replicate the problem with Chromium, I guess that narrows it down. 

I was on Firefox 3.6.8

---

### Post by JBAlaska on 2010-08-25
The dam picture loaded fine for me in firefox.

---

### Post by leoh on 2010-08-25
I'm with a friend next to me, he's running Mandriva (KDE) and Firefox 3.6.8 (the same version we are running), and he doesn't have this problem.

---

### Post by leoh on 2010-08-25
I could also replicate the problem under Xfce on the same computer. This seems to be a Firefox issue.

---

### Post by wojox on 2010-08-25
> **JBAlaska said:**
> The dam picture loaded fine for me in firefox.

Did you click on the picture after it loaded?

---

### Post by Pascal-7 on 2010-08-25
loaded fine for me, and I clicked on it too
edit: using firefox by the way

---

### Post by leoh on 2010-08-25
Seems to be an old unfixed issue:
[http://ubuntuforums.org/showthread.php?t=1288062](http://ubuntuforums.org/showthread.php?t=1288062)

I could not replicate the problem on Firefox 3.6.8 on Windows on the same computer. Seems to be an issue with FF and Ubuntu, but not gnome...?

---

### Post by JBAlaska on 2010-08-25
> **wojox said:**
> **Did you click on the picture after it loaded?**

Yes using Firefox 3.6.8, and I also right clicked and saved it to my box, and opened it with "Eye of GNOME 2.30.0"

I also opened it with Minefield 4.0 (Firefox 4.b4pre) with no problems.

---

### Post by quizno50 on 2010-08-25
I'm using Firefox 3.6.6 on Mac OS X and the picture loaded fine and I was able to click and scroll around. So I don't think the issue is with Firefox. It may be a problem with the jpeg decoding library the Firefox is compiled against?

---

### Post by lovinglinux on 2010-08-26
Works perfectly here with Firefox 3.0.19, 3.5.9, 3.6.8, 4.0b3, 4.0b4, 4.0b5pre. Looks like the problem is on your system.

I recommend testing on Firefox with safe mode or using a new profile. See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

If the steps on that tutorial doesn't help, then create new Ubuntu user, login with that account and test it. If it works, then is probably some Gnome settings messing with Firefox.

---

