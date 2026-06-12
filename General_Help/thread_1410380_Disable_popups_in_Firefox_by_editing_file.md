---
title: "Disable popups in Firefox by editing file"
date: 2010-02-18
forum: General Help
---

### Post by deepyogi on 2010-02-18
hey is anyone aware of how to disable popups in Firefox by editing prefs.js file like the same way you do it by going to Edit-Preferences-Content and unselecting the Block PopUps box. I need to do this through a script thus i need to edit preference file directly. 
thanks.

---

### Post by wojox on 2010-02-18
Try:

```
user_pref("imageblocker.enable", true);
```

---

### Post by deepyogi on 2010-02-18
> **wojox said:**
> Try:

```
user_pref("imageblocker.enable", true);
```

okie thanks a lot for poinitng me in the right direction. above did not work but while i was reading about imageblocker.enable i came across ```
user_pref("dom.disable_open_during_load", false); 
``` and it worked. but now i have another question to ask i made a custom profile that contains this preference in its user.js file. i can start firefox with this profile and can see the popups block option is unselected. all good so far but what i want to do is run a script while running this profile with firefox. let me explain more. so  this opens firefox with desired profile.
```
firefox -P/root/.mozilla/firefox/oscucdwa.customprofile
```and this runs my script well 
```
firefox "javascript:window.open('http://yahoo.com','myapp',toolbar=0,menubar=0);self.close();"
```but i somehow want to combine them together. 
if you can help me this i will aprreciate that a lot. again thanks for you reply earlier.

---

### Post by deepyogi on 2010-02-18
i would appreciate if somebody takes a look

---

