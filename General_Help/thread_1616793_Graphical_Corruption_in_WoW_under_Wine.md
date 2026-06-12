---
title: "Graphical Corruption in WoW under Wine"
date: 2010-11-08
forum: General Help
---

### Post by Nanix on 2010-11-08
When I run WoW through wine there is severe graphical corruption. I am using opengl and have tried windowed/nonwindowed mode. No luck.

Any assistance concerning this?
Here is a pic:
[http://img28.imageshack.us/img28/5004/screenshotworldofwarcra.png](http://img28.imageshack.us/img28/5004/screenshotworldofwarcra.png)
(I am running a w2k theme, this IS linux)

---

### Post by searchfgold6789 on 2010-11-08
I have not investigated this, but there seems to be software addressing this issue called playonlinux, you can get it from the software center.
Or you could VM it.

---

### Post by gyussz on 2010-11-08
Is your graphic card driver installed correctly?
Did you set wine to windows 7 mode? (According to my experiences, Windows 7 mode is the best for WoW)
I know you mentioned you're using opengl, but make sure the config.wtf file contains the following line:
```
SET gxApi "opengl"
```

WoW should run fine with these settings above.

---

### Post by Desiderantes on 2012-03-19
Nanix, even if it's a almost-2 years old thread, i have exactly the same issues. Did you find a solution?

---

### Post by oldos2er on 2012-03-20
Closed, necromancy. Please start a new thread in the Wine subforum for your question.

---

