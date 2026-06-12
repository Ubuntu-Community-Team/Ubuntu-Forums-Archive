---
title: "no spelling suggestions in firefox 3.5.5"
date: 2009-11-12
forum: General Help
---

### Post by prakreet on 2009-11-12
I am using ubuntu 9.10 and firefox 3.5.5. firefox is detecting the spelling errors but not providing any suggestions for correction.. there is only one option "Undo". what's wrong here....

---

### Post by Tiganjero on 2009-11-12
Go into Edit>Preferences>Advanced>General and tick the box next to "Check my spelling as I type".
Hope I helped :P

George

---

### Post by prakreet on 2009-11-15
Spellcheck is already enabled in firefox...

---

### Post by Tiganjero on 2009-11-15
> **prakreet said:**
> Spellcheck is already enabled in firefox...

So sorry, I replied to the title, and completely forgot about the actual question... Anyways, put this in the terminal and post the output ```
dpkg -p firefox-3.0 | grep Version
```

---

### Post by prakreet on 2009-11-16
The firefox version on my comp is not 3.0 but 3.5. So i changed the code and typed 
dpkg -p firefox-3.[FONT=Verdana]5[/FONT] | grep Version 
Its output is:.........
 Version: 3.5.5+nobinonly-0ubuntu0.9.10.1

---

### Post by Tiganjero on 2009-11-16
Hmm, I'd suggest you backup your Firefox data and then delete the Firefox folder, and replace it with a fresh copy... That would surely fix your problem... If you need any help just tell me :P

George

---

### Post by prakreet on 2009-11-16
[B]Bug fix for foxtab 1.2.1
[/B]


  										 
[LIST]
[*] 											 Firefox 3.5 on Linux & Mac - Spell check suggestion is missing when mouse gestures are enabled.
[/LIST]
 
 My problem is solved. Thanx...

---

