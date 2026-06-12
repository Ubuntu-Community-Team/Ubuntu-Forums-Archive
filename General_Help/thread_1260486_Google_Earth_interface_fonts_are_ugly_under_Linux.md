---
title: "Google Earth interface fonts are ugly under Linux"
date: 2009-09-07
forum: General Help
---

### Post by Vunutus on 2009-09-07
Something isn't right. I'd explain it but a picture is worth a thousand words, so:

[IMG]http://img42.imageshack.us/img42/9575/screen1bk.png[/IMG]

It just isn't right at all. I searched for a solution and found several suggestings involving the google earth config file, but they only made things look worse (and even after reverting to the old config file they stayed looking worse).

Is there some sort of magical solution to make the interface look like it does in Windows?

---

### Post by Efwis on 2009-09-07
have you installed the ttf-mscorefonts? these are windows fonts that Linux doesn't have. 
Make sure you have the multiverse repository enabled. Then run 

```
 sudo apt-get update && sudo apt-get install ttf-mscorefonts-installer
```

after they are installed try running GE again and see if that helps

---

### Post by Vunutus on 2009-09-07
> **Efwis said:**
> have you installed the ttf-mscorefonts? these are windows fonts that Linux doesn't have. 
Make sure you have the multiverse repository enabled. Then run 

```
 sudo apt-get update && sudo apt-get install ttf-mscorefonts-installer
```

after they are installed try running GE again and see if that helps

Already installed and at the latest version =/

---

### Post by Efwis on 2009-09-07
since you're running KDE for your desktop, I'm not sure where to go, (strictly a gnome user). hopefully someone with more knowledge on KDE can help ya.

---

