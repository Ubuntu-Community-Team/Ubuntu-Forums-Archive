---
title: "Window titles is not showing"
date: 2009-11-27
forum: General Help
---

### Post by doctorx2009 on 2009-11-27
I don't know what exactly caused that but after update or package removing ? 
now every time ubuntu starts i get windows with no titles i mean no frame/border at all so no menu and the window properties gives error when i click it from the main menu it says something like not registered 

for the border/frame problem i change from no effects(graphics) to normal mode and it fixes that for a while and i can after that return to no effects mode but when i restart the computer same problem again what should i do and if update caused that when should i update when not really confusing :icon_frown:

note : I tried removing and reinstalling compiz and metacity with no help

---

### Post by ajgreeny on 2009-11-27
There are several comments to make about this, but without more info it will be difficult to be sure about what is happening.

What hardware are you running, and is compiz generally running OK?  I think it must be tied up wuth compiz in some way, however, as when you change from no effects to normal things work OK for a while.  Usually it's the other way round!

Install compizconfig-settings-manager (ccsm) and make sure the plugin "Window decoration" in Effects is enabled.  That may sort things out, but if not you may need to play around a bit and see if you can get a combination of settings and plugins that work well with your system.

---

### Post by myoldhouse on 2010-01-11
My problems with lost window decorations occurred under both compiz and metacity and would seem to happen randomly, but once lost, nothing would bring the window decorations back except using "metacity --replace" as one of the startup scripts.

I finally had enough and decided to track this thing down and I found that sitting in my home directory under ./local/share/applications there were two files that were the root cause. One was named compiz.desktop and the other was named metacity.desktop. Deleting, renaming or moving those two files restores normal window decorations under both compiz and metacity.

I don't know what generates those files and puts them there but I know what to do to get window decorations back if they go missing - I look for those two files in ./local/share/applications and I delete them and I'm good until the next time they appear, which could be in days, weeks or months.

Your mileage may vary, but it won't hurt to try this if nothing else works for you in restoring your window decorations under either compiz or metacity.

PS My system is Ubuntu 9.10 AMD64 but I had this problem under 9.04 AMD64 as well and the fix worked for both of them.

---

