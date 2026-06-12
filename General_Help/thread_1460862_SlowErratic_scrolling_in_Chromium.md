---
title: "Slow/Erratic scrolling in Chromium"
date: 2010-04-23
forum: General Help
---

### Post by skelooth on 2010-04-23
Hello, I just upgraded from 8.04 to the lucid beta (yes I was slow to move on that), and chromium's scrolling is HORRID! It jumps and skips both when I use the mouse wheel or when I drag the scroll bar.

Any ideas? Firefox scrolls just fine. It makes using chromium very unpleasant because any time I have to scroll I feel like I'm back in 1992.

I did some searching and found lots of complaints, so I thought I was close to an answer until I looked at the date, it was late 2008/early 2009 when this was an issue.

---

### Post by spiridow on 2010-04-23
Try this extension: [https://chrome.google.com/extensions/detail/khpcanbeojalbkpgpmjpdkjnkfcgfkhb?hl=en-us](https://chrome.google.com/extensions/detail/khpcanbeojalbkpgpmjpdkjnkfcgfkhb?hl=en-us)

---

### Post by skelooth on 2010-04-23
I tried the smooth scrolling extension, and all it does is cause the erraticness to 'smooth its self over', ie, it still sticks and sputters, but there's now a smooth transition between each stutter.

---

### Post by skelooth on 2010-04-23
Wow, fast message board. BUMP. I miss 8.04

---

### Post by kerry_s on 2010-04-23
what chromium version you running?

i got 5.0.386.0 (45407) Ubuntu, i don't notice any problem.

---

### Post by skelooth on 2010-04-26
I'm also running 5.0.386.0 (45407),

It's still a problem but I'm "getting used to it", at first it really hurt to look at. I'd still love to hear any solutions. This is a fresh install on a new quad core. Everything else flies.

---

### Post by pseudocube on 2010-06-24
I am experiencing this problem as well.

Lucid 10.04
Chrome 5.0.375.70 Beta

---

### Post by ajgreeny on 2010-07-18
Has this problem been solved?  I have just tried chromium from the repos on my desktop, and to be honest, it is totally unusable for this slow scrolling.

There are a lot of other problems for me as well, such as tab management, poorer flash performance, bookmark display, which are less important and may be solvable, but the scrolling problem is a showstopper.

---

### Post by antiram on 2010-09-19
it is fixed for my radeon r600 card and compiz with xorg-edgers ppa and gallium3d. the gallium driver is in package libgl1-mesa-dri-experimental and must activated in /etc/enviroment with:
LIBGL_DRIVERS_PATH="/usr/lib/dri/gallium"

---

