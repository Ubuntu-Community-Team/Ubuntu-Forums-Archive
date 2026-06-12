---
title: "Backslash key always types a '&lt;' instead"
date: 2011-07-02
forum: General Help
---

### Post by dadawan on 2011-07-02
I have 10.4 installed on my Asus laptop.  Unfortunately, whenever I hit the backslash key, a less-than character gets typed.  I have checked the keyboard layout via system->Prefs->keyboard, and all looks fine.  This key works fine in Windows.

  How do I fix this?

---

### Post by PCaddicted on 2011-07-02
Do you use the USA keyboard layout or another one?
Or, your problem might have been caused by hardware issues(have you spilled a liquid on your keyboard ?). Something similar happened to me a couple of years ago(but it was much worse) and I realised that it had been caused by some water that I had accidentally spilled on the keyboard.

---

### Post by WorMzy on 2011-07-02
Sounds like you have the wrong keymap enabled. Try running 
```
sudo dpkg-reconfigure console-setup
```

and selecting the correct keymap when prompted.

---

