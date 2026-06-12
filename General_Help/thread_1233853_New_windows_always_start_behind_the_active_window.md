---
title: "New windows always start behind the active window"
date: 2009-08-07
forum: General Help
---

### Post by malanciault on 2009-08-07
Hi,

I'm using Hardy and since a week or 2, whenever I start something new, the window that is created gets displayed behind the active window. For example, I have the OpenOffice Writer open, active and maximized. I select Applications from the Ubuntu menu > Accessories > Calculators. The Calculator window will display behind the Writer window, and the button will appear flashing in the task bar. If I minimize Writer, I will see Calculator. 

So it's not that new apps are starting minimized by default, they always start correctly but get displayed behind the active window. 

This happens with any application that has the active window, I can be in Firefox, Writer, Calc, TweetDeck, whatever, all the same. 

I check, and none of the windows I have opened are set to display "Always on Top", when I right click their button in the task bar.

This is becoming rather annoying ;-). Anyonw can help with this ?

Many thanks!!

---

### Post by wojox on 2009-08-07
If your using compiz check for Place Windows. I had a similar problem and that fixed it.

---

### Post by Katalog on 2009-08-07
This seems to have been a known bug in Unbuntu 8.04 and Debian Sid. Searching around old bug reports, this appears to be the fix for this problem:

Go into gconf-editor
Go to apps>metacity>general
Set the value on "focus_new_windows" to "strict"

Seemed to solve the problem for the majority of users that listed the problem in that particular bug report. Hope this helps.

---

### Post by philinux on 2009-08-07
Yes this got fixed in later releases. Damned annoying.

---

### Post by malanciault on 2009-08-07
Ok I changed it in gconf-editor. It still does not solve the problem. Perhaps I need to restart ?

Thanks for your help !

---

