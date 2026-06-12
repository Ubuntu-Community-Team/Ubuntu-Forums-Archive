---
title: "CNN flash all messed up, but other flash sites ok"
date: 2010-12-15
forum: General Help
---

### Post by sdowney717 on 2010-12-15
[http://www.cnn.com/2010/US/12/15/winter.weather/?hpt=T2](http://www.cnn.com/2010/US/12/15/winter.weather/?hpt=T2)

as you can see from the picture, it is not correctly displayed.

---

### Post by philinux on 2010-12-15
Plays fine here even full screen in Firefox. 64 bit with 64 bit flash.

---

### Post by sdowney717 on 2010-12-15
that is nice for you.
I just checked with Chrome and get the same type of messed up image.

---

### Post by sdowney717 on 2010-12-15
it has been messed up on CNN for about a week, but I just posted to show any interested people what it looks like.
ALSO, full screen is acting strange, frequently wont full screen, sometimes nothing, sometimes I got the flash box black and hear the video, sometimes if I minimize the browser, i will see it playing full screen on the desktop and no interaction of controls can affect it.

---

### Post by philinux on 2010-12-15
> **sdowney717 said:**
> it has been messed up on CNN for about a week, but I just posted to show any interested people what it looks like.
ALSO, full screen is acting strange, frequently wont full screen, sometimes nothing, sometimes I got the flash box black and hear the video, sometimes if I minimize the browser, i will see it playing full screen on the desktop and no interaction of controls can affect it.

Is this 32 bit? Something odd going on for you then.

---

### Post by TeoBigusGeekus on 2010-12-15
Opera 10.63 on Arch 32bit here, plays fine.
Try deleting .adobe and .macromedia folders in your /home partition.

---

### Post by sdowney717 on 2010-12-15
yes 32 bit latest ubuntu updated etc...

tried  deleting those folders but no diff
also just uninstalled and reinstalled flash but no diff

could it be the video driver?
likely not but why is this only a problem on cnn?

---

### Post by ajgreeny on 2010-12-15
Plays fine here on 32 bit 10.04 with open source ATI/radeon driver for the 9200SE card.  I'm using the Adobe flash 10.2 beta version downloaded direct from Adobe, but I don't know if that will make any difference.

---

### Post by sdowney717 on 2010-12-15
well just tried the 10.2 and no diff. I verified I am using it

hmmm, just tried Opera and it is fine.
Still messed up with chrome and firfox

---

### Post by efflandt on 2010-12-15
Do you have more than one type of flash plugin installed, like gnash or swf or anything, instead of just flashplugin-installer.  The cnn link works fine for me in Maverick Firefox w/real 64-bit flash, embedded or full screen (nvidia 2.60.19.26 drivers from x-swat) with a new video card model that lspci does not even list the model of (GT 430).

Maybe this would help [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) or search the forums for "flash video" for other ideas.

---

### Post by sdowney717 on 2010-12-15
only the one adobe flash plug in is installed,

---

### Post by sdowney717 on 2010-12-15
tried that add on, ity reverted it back to 10.1
and the cnn flash is still messed up.

---

### Post by sdowney717 on 2010-12-15
figured out something.
I logged in using a new user and the flash WORKS FINE.

this firefox does not have addblock.
so what would affect both chrome and firefox?
on chrome I run adthwart.

Added on adblock to the new user account and flash is still fine.

---

### Post by sdowney717 on 2010-12-15
I logged back in to my original user account
Disabled addblock
and flash is still messed up.

So, there must be something going on with my user settings related to cnn??

as an update jan7, 2011
flash completely crashes firefox all the time on most every site, excpet for google news, those little tiny video boxes on th right hand side.
oddly chrome also had some flash glitches
weird!

So i deleted the profile, made a new firefox profile, restored the bookmarks
flash now is working like it should on all pages.

---

