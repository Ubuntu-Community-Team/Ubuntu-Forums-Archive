---
title: "UI in 10.04 is sluggish"
date: 2010-08-03
forum: General Help
---

### Post by intrader on 2010-08-03
These are the problems that I have observed:
1. Slow responding to clicks - Test in Mouse Preferences demonstrates it readily; the light bulb does not always light up on first click.
2. Activation of alternate window takes more than one click
3. Click on scrollbar's botton arrow remains activate and continues to move even when mouse is lifted.
4. Scrollbar randomly remains active after click on scrollbar's middle (floating) button even if mouse is move to the window area.
5. After a click on icon or link, often mouse icon changes to a hand icon and the icon moves with the mouse. Difficulty unloading this action - takes several clicks.
6. Highlighting is difficult to cancel once it starts.

This problems started with an update in 9.10 to X (which I was trying). Make the system very unusable.

:(

---

### Post by ajgreeny on 2010-08-03
Could be a graphics driver problem but with no hardware information it is impossible to say more.

---

### Post by intrader on 2010-08-03
> **ajgreeny said:**
> Could be a graphics driver problem but with no hardware information it is impossible to say more.

Sorry. 
The graphics card (NVIDIA) is running the 'NVIDIA accelerated graphics driver - version 96.
The machine is a Dell Inpiron 8200 with 1 GB of memory (its max).
The problems with slcuggish UI appeared in Ubuntu 9.10 _once the X update was automatically installed_.
Perhaps the problems have to do with the multiple gestures code added to X.

---

### Post by ajgreeny on 2010-08-04
OK, thanks for the info.

I don't know about nvidia specifically, but I do know that from 9.10 on, older ati graphics cards had some difficult problems with the open source driver, the only driver available for those cards.  Previously the card I have (9200SE) was great with Ubuntu, but the two most recent versions, 9.10 and 10.04, have been much poorer in graphics performance and need a lot of xorg.conf tweaking.

Perhaps the same is true for you, though I thought nvidia was much better than ati these days.  Have a look in **System ->Administration ->Hardware Drivers** and see if there is another driver to try.

---

### Post by intrader on 2010-08-04
I have removed the driver (version 96) and rebooted.
It seems better as shown below:
1. Slow responding to clicks - Test in Mouse Preferences demonstrates it readily; the light bulb does not always light up on first click. -----> all clicks work.
2. Activation of alternate window takes more than one click ---> better
3. Click on scrollbar's botton arrow remains activate and continues to move even when mouse is lifted.  ----> works
4. Scrollbar randomly remains active after click on scrollbar's middle (floating) button even if mouse is move to the window area.  ----> better; the scrollbar remais active, but it easily cancelled
5. After a click on icon or link, often mouse icon changes to a hand icon and the icon moves with the mouse. Difficulty unloading this action - takes several clicks.  ----> works
6. Highlighting is difficult to cancel once it starts.  ----> works

It appears that removing the updated driver betters the UI reponses. I will be testing more. 

10.04 UI is still sluggish - for example 
1. clicking on Close button of the Mouse Preferences takes several tries.
2. clicking on Previous of a PDF document viewer.
More problems, but less extreme as with the updated driver:
1. click on icon or link sometimes after a moment, converts to the hand pointer with an icon representing the icon or link.
2. click on scrollbar to cause scroll is sluggish.

Spoke too soon:
Eventhough it feels faster, it exhibits the same original problems as described above. It is not the driver.


Continued testing
Thanks

---

