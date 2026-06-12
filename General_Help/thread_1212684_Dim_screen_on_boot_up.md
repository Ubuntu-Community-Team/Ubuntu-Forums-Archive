---
title: "Dim screen on boot up"
date: 2009-07-14
forum: General Help
---

### Post by Cthulhu_Dreams on 2009-07-14
Simple problem with a simple solution I'm sure.  I'm on a laptop and when Ubuntu begins its boot up process, the screen dims (I assume because it recognizes that its a laptop and could theoretically be on battery power).  Is there anyway I can change it so it only does this when I genuinely am running off of my battery, or if necessary just make it so it always stays at full brightness?

---

### Post by Cthulhu_Dreams on 2009-07-14
bump

---

### Post by Cthulhu_Dreams on 2009-07-15
Bump

---

### Post by rhchia on 2009-07-15
hmm... normally i'll use the function key on the keyboard to adjust the brightness.

---

### Post by Cthulhu_Dreams on 2009-07-18
I don't think that'd permanently solve the problem though....

---

### Post by Cthulhu_Dreams on 2009-07-24
BUmp

---

### Post by Finalfantasykid on 2009-07-24
Have you checked your Power Settings?

System > Preferences > Power Management

You can set your LCD brightness for both on AC and on Battery there.

---

### Post by Cthulhu_Dreams on 2009-07-24
No, those are fine, its specifically a boot issue.

---

### Post by Finalfantasykid on 2009-07-24
Ok this is maybe a longshot, but try typing...

```
sudo gconf-editor
```then go to...
apps > gnome-power-management > backlight 

See what it says for brightness_ac.  If it is not 10, then bump it up to 10.  

This might now work, since it might just be linked with what you already tried.

EDIT:  You could also probably check your BIOS since you can usually adjust your default LCD brightness settings there.

---

### Post by Cthulhu_Dreams on 2009-07-30
Nothing in the BIOS that allows LCD adjustment, the setting you told me to look at was at 100.

---

### Post by Peedjay on 2009-08-07
Same here. Most of the times my screen dims when I'm halfway trough boot-up (even when on AC). Quite annoying if your login screen is hardly readable. Somebody a solution for this? My power management settings are all fine.:confused:

---

