---
title: "Close, minimize, maximize buttons"
date: 2010-06-21
forum: General Help
---

### Post by thefallofroy on 2010-06-21
The fact that they are on the left side of the windows in 10.04 is really frustrating for me. Please tell me there's a way to move them back to the right were they belong...

---

### Post by lisati on 2010-06-21
The answer is here in the forum. Amongst other places you might want to look at [http://ubuntuforums.org/showthread.php?t=1423882](http://ubuntuforums.org/showthread.php?t=1423882)

---

### Post by thefallofroy on 2010-06-21
Thank you very much!

---

### Post by thefallofroy on 2010-06-21
Sorry to be a nit pick, but is there any way to put the minimize button on the left instead of being in the center?

---

### Post by TechnikAlsace on 2010-06-21
Instead of using the gconf configurantion string 
"menu:maximize,minimize,close" 
as indicated in most tutorials just play around with the order of "maximize", "minimize" and "close" and see what happens. Not all themes will accept the minimize button in the first place, so it's a bit of a trial and error story

---

### Post by thefallofroy on 2010-06-21
> **TechnikAlsace said:**
> Instead of using the gconf configurantion string 
"menu:maximize,minimize,close" 
as indicated in most tutorials just play around with the order of "maximize", "minimize" and "close" and see what happens. Not all themes will accept the minimize button in the first place, so it's a bit of a trial and error story

You are a genious good sir, i switched this 
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:maximize,minimize,close" to this
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"

---

### Post by OtakuWrath on 2010-06-21
simply download [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) open it and go to the last option.. it lets you freely choose left or right..

---

### Post by philinux on 2010-06-21
Please see the General Help forum sticky for the correct method.

---

### Post by wojox on 2010-06-21
You should use this:

1. System > Preferences > Appearance
2. Select the theme icon &#8220;New Wave&#8221;
3. Click the button &#8220;Customize..&#8221;
4. Select tab &#8220;Controls&#8221; and select &#8220;Ambiance&#8221;
5. Select tab &#8220;Window border&#8221; and select &#8220;Ambiance&#8221;
6. Select tab &#8220;Icons&#8221; and scroll down and select &#8220;Ubuntu-mono-dark&#8221;
7. Select &#8220;Save Theme&#8221; to your choice.

Check out my web page.

---

