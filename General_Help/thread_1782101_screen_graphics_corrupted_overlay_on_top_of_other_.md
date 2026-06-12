---
title: "screen graphics corrupted overlay on top of other app windows"
date: 2011-06-14
forum: General Help
---

### Post by scottstensland on 2011-06-14
Once I launch google chrome

       14.0.792.0 (Developer Build 88942 Linux) Ubuntu

(problem happens across various 
chrome versions and firefox too)

and I visit a site with graphics, still image or youtube,
I get a screen overlay of the website image positioned
near top left of my monitor which overlays its graphics
on top of windows of other applications.
Interestingly, when I kill chrome the image disappears, then
reappears on re-launch of chrome.  Somehow chrome is controlling the rendering of its video memory, from killed tabs, outside of its own window.  

This I have seen for firefox as well.  Its been happening for few months, not on every browser launch but daily nonetheless.  
The video corruption also prevents mouse cursor cut N paste of text on any application which happens to have its window overlayed in this manner. 

I have all the latest updates

ubuntu 11.04 
nvidia driver 270.41.19

screen captures of offending overlay do not show up, though
I could photograph my screen if need be.  Have stopped using
beta chrome daily builds, now using default google chrome to verify
whether symptoms disappear.

I see no apparent errors in system log or X server log
Any suggestions ?

---

### Post by scottstensland on 2011-06-15
I reverted back off the daily beta google chrome builds, now using default chrome install and all OK

---

### Post by baccilus on 2011-07-31
I seem to have this problem too. I have the latest version of Chrome (12.0.742.112) on fully updated Ubuntu 10.10. I have a HD 4670 with proprietary driver.
I nearly always get this problem on Chrome. Only way to resolve is to logout and then login again.

---

