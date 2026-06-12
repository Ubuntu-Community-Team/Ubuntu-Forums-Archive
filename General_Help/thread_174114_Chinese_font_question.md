---
title: "Chinese font question"
date: 2006-05-11
forum: General Help
---

### Post by tsb on 2006-05-11
I installed two sets of recommended Chinese CT/TT fonts but all my chinese fonts look the same.  Where can I check which fonts are being used to display Chinese characters?  Or do I change all my fonts in the font settings to one of these font sets?

---

### Post by njf on 2006-05-12
See [http://ubuntuforums.org/showthread.php?t=125811&highlight=chinese+font](http://ubuntuforums.org/showthread.php?t=125811&highlight=chinese+font)

---

### Post by tsb on 2006-05-12
where is font substitution in kcontrol?  qt-qtconfig isn't needed in kde according to adept.

I installed it anyway, I'll reboot and check it out

---

### Post by njf on 2006-05-12
It's qt3-qtconfig.
You can set fonts in "System Settings" >> "Appearance" >> "Fonts".
If you want to use chinese font but also want nice looking western font, set the western font you want in the "System Settings". 

Then go to KMenu >> "Settings" >> "Qt3 Configuration" and set the chinese font as a substitution font.

See my screenshots for an example.

---

### Post by tsb on 2006-05-12
I did that but the Chinese still looks terrible.

I am using AR PL KaitiM Big5 and AR PL KaitiM GB in the replacement section.  Are these fonts bad or do I need to adjust something else?  I noticed you are using AR PL ZenKai Uni.  Is that for both traditional and simplified Chinese?  Thanks.

---

### Post by njf on 2006-05-12
You need to restart the kde apps for it to take effect. Or you can logout kde and login again.

---

### Post by tsb on 2006-05-12
did that, any other ideas

---

### Post by shanghaielaine on 2006-09-26
> **njf said:**
> It's qt3-qtconfig.
You can set fonts in "System Settings" >> "Appearance" >> "Fonts".
If you want to use chinese font but also want nice looking western font, set the western font you want in the "System Settings". 

Then go to KMenu >> "Settings" >> "Qt3 Configuration" and set the chinese font as a substitution font.

See my screenshots for an example.


Hey, 

I have a dumn question, how can I find the "Qt3 Cinfiguration? It's not im my Kmenu.

---

