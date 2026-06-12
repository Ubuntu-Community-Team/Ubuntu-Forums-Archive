---
title: "Firefox not using system fonts"
date: 2009-11-09
forum: General Help
---

### Post by GHowlerson on 2009-11-09
Hi all,

I've just installed MS sharp fonts, which has made my Ubuntu experience much easier on the eye. But for some reason Firefox isn't using the system fonts (everything else is, looks great). 

Any idea why not and how to fix?

TIA

---

### Post by Derspankster on 2009-11-09
In Firefox, Edit>Preferences>Content>Advanced>Check the box that says Allow pages to choose their own fonts....

That should do it.

---

### Post by winotree on 2009-11-09
If that doesn't work, this is a distillation of a few posts that helped several users, including me -- it'll make Firefox use the preferences in Appearance | Fonts [or whatever it's called in your distribution].
```
sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig 
```

---

### Post by sarble on 2010-03-25
I know this is months late, but I've just come across winotree's post and wanted to say thanks - that does exactly what I want :)

---

