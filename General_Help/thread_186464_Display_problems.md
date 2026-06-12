---
title: "Display problems"
date: 2006-06-02
forum: General Help
---

### Post by yusufm on 2006-06-02
After upgrading to dapper, most buttons have weird visual artifacts on them till you hover over them, and then they clear up. See the attached image. Also the screen sometimes flickers on-off suddenly. This did not happen in breezy.

Thanks.

---

### Post by mattisking on 2006-06-02
I just did a fresh install. I'm not seeing quite that effect, but I have noticed that sometimes the buttons just black out until I hover over them. I had thought, however, that this might just be the fact that I haven't yet switched over to the fglrx (ATI proprietary) drivers and am still currently running the default "ati"... If I can catch it, I'll screenshot it and stick it up there as well.

Update: That didn't take long... Here's a screenshot.. of me taking a screenshot. Notice the "blue" Help button. All 3 buttons were blue until I moused over them.

---

### Post by kmkittre on 2006-06-02
I, too, am having this problem.  I am running ubuntu 6.06 on a compaq laptop with an ati video card.  I'm assuming this is just an X11 tweak?

---

### Post by btlee on 2006-06-02
What is your color depth, 16 or 24?
It seems to be a shortage of color depth, but just my guess.

---

### Post by ]TheNose[ on 2006-06-02
Yusufm is having the same problem as I've been experiencing. More information about the problem can be found at the thread I had already opened:
[http://www.ubuntuforums.org/showthread.php?p=1076413]("http://www.ubuntuforums.org/showthread.php?p=1076413")

Apparantly the problem is caused by some combinations of ati + the xorg driver + cairo.

Still, they haven 't found a solution for it yet.:(
The official bugreport can be found here:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/34435]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/34435")

---

