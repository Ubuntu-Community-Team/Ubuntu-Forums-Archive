---
title: "Default Browser - Chromium"
date: 2010-02-21
forum: General Help
---

### Post by TheBuda on 2010-02-21
Not sure if anyone can point me in the right direction.  I just get up my netbook, and installed Firefox just to get up and running and pull some tutorials and guides.  I then installed chromium and removed Firefox using aptitude.  Now Firefox was removed, chromium works great, but I can get Chromium to be the default browser.  I've said to make it the default browser every time I open it, and I've gone into Options -> Basics and the button does nothing.

Any advice?

---

### Post by Darkish Dave on 2010-02-21
> **TheBuda said:**
> Not sure if anyone can point me in the right direction.  I just get up my netbook, and installed Firefox just to get up and running and pull some tutorials and guides.  I then installed chromium and removed Firefox using aptitude.  Now Firefox was removed, chromium works great, but I can get Chromium to be the default browser.  I've said to make it the default browser every time I open it, and I've gone into Options -> Basics and the button does nothing.

Any advice?

Yep. Go to System > Preferences > Preferred Applications

If Google Chrome is not on the list use the custom command

```
google-chrome %s
```

---

### Post by Darkish Dave on 2010-02-21
Or try, Open Chrome, Open Options, click the Basics Tab and click 'Make Google Chrome My Default Browser"

---

### Post by bodhi.zazen on 2010-02-21
From the command line :

sudo update-alternatives –config x-www-browser 

Not sure if this applies to Chromium ^^

From the graphical interface :

System -> Preferences -> Preferred Applications

---

### Post by TheBuda on 2010-02-21
The system -> preferences -> preferred apps worked, thank you.  Chromium stil insists its not the default browser, but links open chromium and I was able to tell if to stop asking me.

thanks all.

----  Solved ----

---

