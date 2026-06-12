---
title: "maximize start screen chrome/chromium"
date: 2012-01-07
forum: General Help
---

### Post by speed32219 on 2012-01-07
I can not get Chrome or Chromium-browser to start in full screen from the CLI.  I have added the switches and it still does not fill my 21" wide screen. (Only half the screen)  FF is no problem, but since I only use fluxbox as a WM, I can not get it to work.

This command string will start Chrome and Chrome-browser, but no full screen.  F11, alt + enter, nothing works.

 DISPLAY=":0.0" chromium-browser --start-maximized "www.uverseonline.com"

---

### Post by speed32219 on 2012-01-08
Bump

---

### Post by llelectronics on 2012-01-08
Just add those lines to your ~/.fluxbox/apps file 

```
[transient] (name=chromium-browser)
      [Maximized]	{yes}
[end]
```

This should open every chromium windows maximized.

---

### Post by speed32219 on 2012-01-08
Thank you for the info, since it works with FF 3.0.6 I never thought adding that string to the fluxbox app.  I added it and still will not go full screen.  

I have tried Chrome and Chromium Beta's and still no joy.  If I go to crackle and start a show it does go full screen, its like the broswers do not support wide screen monitors, or at least do not work with the proper switch set as posted previously.

---

