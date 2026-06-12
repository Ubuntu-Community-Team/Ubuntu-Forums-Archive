---
title: "Refresh rate"
date: 2009-12-04
forum: General Help
---

### Post by KommerszUnicum on 2009-12-04
Hi Guys!

I'd like to change my refresh rate on 9.10. If I create a xorg.conf is it enaugh to put the monitor info to it? Because I don't have previous xorg.conf and it won't be good if I have to fully recreate it.

Thank you!

KommerszUnicum

---

### Post by IllegalCharacter on 2009-12-04
If you're using compiz:
1) Install compiz config (skip this step if it is installed already): Applications->Ubuntu Software Center, search for ccsm, install the "Advanced Desktop Effects Settings".
2) Go to System->Preferences->Advanced Desktop Effects Settings
3) Click General Options (should be in the middle of the top row)
4) Click the Display Settings tab.
5) Uncheck "Detect Refresh Rate".
6) Fiddle with the refresh rate slider.

---

### Post by KommerszUnicum on 2009-12-04
Thanks your answer! Could you tell me how can I save my changes because it is still 75 Hz but show me 85?

---

### Post by IllegalCharacter on 2009-12-04
When you type into the box, you need to click somewhere and it will adjust the slider. Otherwise it will automatically update things.

---

### Post by KommerszUnicum on 2009-12-04
Sorry, I mean when I set the slider to 85 Hz, the refresh rate doesn't change to it. How can I save the setting?

---

### Post by JoePits on 2009-12-04
> **KommerszUnicum said:**
> Sorry, I mean when I set the slider to 85 Hz, the refresh rate doesn't change to it. How can I save the setting?

try running in a terminal

sudo gnome-display-properties

---

### Post by KommerszUnicum on 2009-12-04
No luck because the display-properties only shows me the 75 Hz for 2048x1024, but thanks.

---

### Post by IllegalCharacter on 2009-12-04
Maybe your system doesn't support higher than 75Hz at that resolution.

---

### Post by KommerszUnicum on 2009-12-05
Thank you guys! I've checked it on W*nd*ws and there is no higher refresh rate on 2048x1024.

---

### Post by KommerszUnicum on 2009-12-12
Hi Guys!

I've switced back to 1024x768 and I know that my monitor has the 100 Hz on that resolution but I could not change it.

Do you have any other idea how can I change the refresh rate?

Thanks!

---

