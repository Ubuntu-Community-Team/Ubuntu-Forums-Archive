---
title: "ubuntu randomly freezes"
date: 2011-07-26
forum: General Help
---

### Post by louisgonick on 2011-07-26
I've had ubuntu for almost 2 months... It worked pretty much out of the box except for some issues with my wireless card. But the UI just happens to randomly freeze while I use it. One time I left my machine on while I went out, when I was back the screen was frozen, the mouse moved but everything else just froze. That happens when I try to change the resolutions of games to fullscreen and it had also been happening when I try to search on wikipeda. The only solution is to shut it off. Anybody else have this issue?? 
Any help is appreciated.

---

### Post by wildmanne39 on 2011-07-26
Hi, start by looking at this link on freezing issues.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by louisgonick on 2011-07-26
> **wildmanne39 said:**
> Hi, start by looking at this link on freezing issues.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Thanks for the advice, but this left me more confused than before. Should I report the bug to ubutnu??? what should I do?

---

### Post by wildmanne39 on 2011-07-26
Hi, first I would open screensaver and set the screen saver to never come on and while in there click on power management set never put computer to sleep and display to sleep.

Also if it freezes again as soon as you boot run this command
```
dmesg |tail -n300
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by louisgonick on 2011-07-26
> **wildmanne39 said:**
> Hi, first I would open screensaver and set the screen saver to never come on and while in there click on power management set never put computer to sleep and display to sleep.

Also if it freezes again as soon as you boot run this command
```
dmesg |tail -n300
```and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

should I make my computer freeze right now?? to get the outcome of that command?

---

### Post by wildmanne39 on 2011-07-26
Hi, after you change the settings in screensaver yes you can try to make it freeze.
Also run this command and post the results here.
```
sudo lshw
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Aeighty on 2011-07-26
Had this happen when downgrading to 10.04. but after some trial and error i belive it was due to a malfunctioning graphics card or the card overheating. when mine froze i could do nothing.

---

