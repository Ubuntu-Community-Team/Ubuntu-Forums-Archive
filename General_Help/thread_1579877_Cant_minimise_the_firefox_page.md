---
title: "Cant minimise the firefox page"
date: 2010-09-22
forum: General Help
---

### Post by ex-para on 2010-09-22
I am using ubuntu 8.10 and firefox 3.0.png and for some reason I cant minimise the firefox page and it is taking up most of the screen. None of the top bar with Applications Places and System or date volume in fact no top bar. I cant remember everything I have tried. When I go to custom the top bar briefly appearers and then goes off. I don't have full page activated so please any advice.

---

### Post by Sin@Sin-Sacrifice on 2010-09-22
Not sure from your explanation but it sounds like the window manager crashed. Try ```
metacity --replace
``` in a terminal or in Run Application dialog via alt+F2. That should bring back the title bar so you have your minimize button. By the way... .png files are pictures.

---

### Post by lovinglinux on 2010-09-22
Have you tried to click F11 twice?

---

### Post by ex-para on 2010-09-23
Thanks for the replies, yes I have a picture at start up. I got nothing with F11, Alt F2 turned my wireless connection off, metacity ---replace put the bar back on but each time I shut down and boot up the bar has gone again. Also with no bar I am unable to paste from the page.

---

### Post by lovinglinux on 2010-09-23
> **ex-para said:**
> Thanks for the replies, yes I have a picture at start up. I got nothing with F11, Alt F2 turned my wireless connection off, metacity ---replace put the bar back on but each time I shut down and boot up the bar has gone again. Also with no bar I am unable to paste from the page.

Add metacity --replace to your Startup options.

---

### Post by ex-para on 2010-09-25
That did it as it is OK now.
Thanks again.

---

