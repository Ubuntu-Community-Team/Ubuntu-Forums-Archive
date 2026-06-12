---
title: "Newb With 11.04 Desktop Problem"
date: 2011-05-01
forum: General Help
---

### Post by FLHRCI99 on 2011-05-01
Hey Everyone,

Just installed Ubuntu 10.10 last week for my first Linux experience. I was starting to become familiar with it when 11.04 came along and I decided to go for the update. The install went smooth and I was surprised how different the desktop looked after the update. The new launcher bar was on the left side of the screen and my Home and Computer icons were still on the desktop. The rest of my desktop icons were gone and only two icons remained on the Cairo-Dock launcher at the bottom of my screen after the update. I was poking around in Applications and found my Compiz program to make some mods I had with 10.10. One of them was Desk Cube for switching screens. Not sure if I mistakenly check marked another box while looking around but after I closed Compiz everything on my desktop was gone! Only the two desktop icons and my wallpaper remained. The launch bar, screenlets, cairo-dock and panel at the top of the screen all disappeared. Does anyone know how I can bring the desktop back to post-update (11.04) condition? I don't know how to access anything with only the Home and Computer icons as I only have a couple hours experience with Ubuntu so far. Any help would be greatly appreciated  :confused:

Bob

---

### Post by remarkrab on 2011-05-01
Try to reset Unity. At the log in screen, after you enter your password and before you actually log in, look at the bottom you can then choose the "classic" desktop. In terminal type:

 ```
unity --reset
```

---

### Post by FLHRCI99 on 2011-05-01
> **remarkrab said:**
> At the log in screen you can change to classic desktop

Any other way to change to classic desktop? I don't have a log-in that comes up after booting or wake-up. I did on 10.10 but stopped it just before updating because it popped up so often. Thanks.

Bob

---

### Post by remarkrab on 2011-05-01
Try ctrl + alt + f1 to access terminal. Then try to reset it. * Then ctrl + Atl +f7 to get back into desktop. I tried it on mine but when exiting terminal to get back into desktop the screen was all screwy like colored snow. I was able to mouse toward the upper right and the shutdown menu came up and was able to log out and back in and it worked fine then.

---

### Post by FLHRCI99 on 2011-05-01
> **remarkrab said:**
> Try ctrl + alt + f1 to access terminal. Then try to reset it. * Then ctrl + Atl +f7 to get back into desktop. I tried it on mine but when exiting terminal to get back into desktop the screen was all screwy like colored snow. I was able to mouse toward the upper right and the shutdown menu came up and was able to log out and back in and it worked fine then.

Thank you. I had to hit the sack for work tomorrow but I'm looking forward to trying your tip the minute I get home. Really appreciate it and I'll post how it goes after I give it a try. :)

---

### Post by FLHRCI99 on 2011-05-05
> **remarkrab said:**
> Try ctrl + alt + f1 to access terminal. Then try to reset it. * Then ctrl + Atl +f7 to get back into desktop. I tried it on mine but when exiting terminal to get back into desktop the screen was all screwy like colored snow. I was able to mouse toward the upper right and the shutdown menu came up and was able to log out and back in and it worked fine then.
 
After talking with a couple friends who were having 11.04 troubles of their own I felt like I probably had a bad install, so I wiped and reinstalled 11.04. It has been working great and I'm now using the Ubuntu Classic desktop. Just have to get a few drivers reinstalled and I'll be good to go. Thanks for your help :)

---

### Post by KazukiFlame on 2011-05-05
i still couldn't get screenlets working however.

---

