---
title: "problem with dual displays"
date: 2012-04-12
forum: General Help
---

### Post by lallijons on 2012-04-12
i was installing ubuntu 11.10 yesterday and when i loged in to my user i had dual displays working well
 but than i installed some recommended updates (graphics card drives) nvidia and now display settings is only shownig me one unknown display how can i get back my old settings 
thanks for your help sincerely a linux noob

---

### Post by Eirreann on 2012-04-12
> **lallijons said:**
> i was installing ubuntu 11.10 yesterday and when i loged in to my user i had dual displays working well
 but than i installed some recommended updates (graphics card drives) nvidia and now display settings is only shownig me one unknown display how can i get back my old settings 
thanks for your help sincerely a linux noob

Yeah, I had the exact same problem!  I almost regret upgrading!  Now, are you using a laptop plugged into a monitor or two monitors from a desktop?  If it's a laptop, you can get it to run on the monitor by going to Settings-->Additional Drivers and installing the Version-96 drivers (not the post-release updates one) and the computer will use the plugged-in monitor instead of your laptop's screen.
I still haven't found a way to get both monitors working at the same time; unfortunately it's just a bug in Ubuntu 11.10; I'm hoping it will be fixed in 12.04

---

### Post by lallijons on 2012-04-12
i'm using two monitors from a desktop

---

### Post by Eirreann on 2012-04-12
> **lallijons said:**
> i'm using two monitors from a desktop

Ah, okay...  I take it that your computer has an Nvidia video card, correct?  If so, go into Dash Home and type in "Nvidia"; Nvidia X Server Settings should come up, click that.  Then in the window that comes up go into "X Server Display Configuration", and there *should* be an option to enable TwinView....
If there isn't then you have the same problem that I do, and Ubuntu can't properly sense your video card.  If that is the case you'll have to do the same as me and hope that the 12.04 upgrade will fix those problems...
What video card do you have, just out of curiosity?

---

### Post by wyliecoyoteuk on 2012-04-12
Funnily enough, I had similar problems until I upgraded!
I'm using the version 173 drivers now.

---

### Post by lallijons on 2012-04-12
it only says "Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0."

it is strange i can see both my monitors (dfp-0-(philips ftv) and dfp-1-(acer Al1951))

im using geforce 9600 gt

---

### Post by Eirreann on 2012-04-12
> **lallijons said:**
> it only says "Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0."

it is strange i can see both my monitors (dfp-0-(philips ftv) and dfp-1-(acer Al1951))

im using geforce 9600 gt

Okay, I was afraid of that... all I can recommend is going into settings-->Additional Drivers and trying to update to one of those drivers.  If you aren't already using it, try updating to the Version-173 driver.

---

### Post by lallijons on 2012-04-12
i'll try that thanks alot the help

---

