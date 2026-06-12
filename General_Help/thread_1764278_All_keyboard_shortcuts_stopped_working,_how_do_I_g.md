---
title: "All keyboard shortcuts stopped working, how do I get them back?"
date: 2011-05-21
forum: General Help
---

### Post by SwingKid on 2011-05-21
As the thread title explains. I upgraded to 11.04, and now I'm using Ubuntu Classic. I still have a problem though and that is that all my keyboard shortcuts are gone. It is especially annoying that the Alt+Shift (flipping between programs running on your desktop) and Super+A (choosing between all programs which are open despite what desktop they are on) are gone. This makes it extremely difficult for me to use my computer atm. How do I get them back? This has nothing to do that it is Unity settings since in Unity you open the terminal also with Ctrl+Alt+T..and that command is not working for me either.

---

### Post by Mr. Shannon on 2011-05-21
Click on the power button and choose **System Settings** then choose **Keyboard Shortcuts** and make sure the shortcuts you want to use are not disabled and that they are mapped to the correct keys.

---

### Post by SwingKid on 2011-05-21
> **Mr. Shannon said:**
> Click on the power button and choose **System Settings** then choose **Keyboard Shortcuts** and make sure the shortcuts you want to use are not disabled and that they are mapped to the correct keys.

It is not that. The terminal should open with Ctrl+Alt+T, as usual, it says - but it doesn't. What can then be the error?

---

### Post by Mr. Shannon on 2011-05-21
Have you tried checking to make sure those keys work and are read correctly.  Go to a terminal and type in ```
xev
``` then verify that Ctrl is giving you keycode 37, Alt is giving you keycode 64, and that t is giving you keycode 28.

Note: If you are not using USA layout then these may not be the correct codes for you.

---

### Post by SwingKid on 2011-05-21
Nothing happened when I tried to click these keys after everything had been written down. It was also a white smaller window opening. A lot of weird text was opening up and nothing said I think what you were writing to me. I have a Swedish keyboard.

---

### Post by Mr. Shannon on 2011-05-21
Have you made sure that under **Keyboard** (search for it in Unity) that the layout is set to Swedish.

Other than that I have no idea.  Will someone else help this person.

Sorry I could not help more.

---

### Post by SwingKid on 2011-05-21
> **Mr. Shannon said:**
> Have you made sure that under **Keyboard** (search for it in Unity) that the layout is set to Swedish.

Other than that I have no idea.  Will someone else help this person.

Sorry I could not help more.

Yep, it is set to Swedish, otherwise I would not be able to write my Öö Ää Åå. :)

I really need some help here. Please, anyone? :confused:

---

