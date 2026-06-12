---
title: "Close, minimize and maximize buttons at wrong side"
date: 2010-11-16
forum: General Help
---

### Post by Lancro on 2010-11-16
You may think, oh thats easy one, no, I dont want the buttons at the  right side, as in windows, I liked them at the left, but when I choose  GTK in compiz fusion, they go to the right side as in windows, they only  work at the left side using emerald, but no with GTK, someone can help me to keep the buttons at the left?, I dont know why they have changed to right side...

Thanks.

---

### Post by Verbeck on 2010-11-16
open gconf-editor (alt+F2 to bring up the run dialogue) 
navigate to /apps/metacity/general
change the value of 'button_layout' to menu:minimize,maximize,close


hope this helps

---

### Post by oopsie on 2010-11-16
> **Verbeck said:**
> open gconf-editor (alt+F2 to bring up the run dialogue) 
navigate to /apps/metacity/general
change the value of 'button_layout' to menu:minimize,maximize,close


hope this helps

That would move them to the right, he wants them to the left.

So, I'd guess he'd have to swap around where you wrote "menu:minimize,maximize,close", to "close,maximize,minimize:menu" or something.

---

### Post by Lancro on 2010-11-16
> **Verbeck said:**
> open gconf-editor (alt+F2 to bring up the run dialogue) 
navigate to /apps/metacity/general
change the value of 'button_layout' to menu:minimize,maximize,close


hope this helps

Thanks but its already set to menu:minimize,maximize,close they were warking on the left side but suddently they have gone into the wrong side..., any other ideas?

Thanks.

---

### Post by oopsie on 2010-11-16
> **Lancro said:**
> Thanks but its already set to menu:minimize,maximize,close they were warking on the left side but suddently they have gone into the wrong side..., any other ideas?

Thanks.

Try what I wrote above =)

---

### Post by Lancro on 2010-11-16
> **oopsie said:**
> That would move them to the right, he wants them to the left.

So, I'd guess he'd have to swap around where you wrote "menu:minimize,maximize,close", to "close,maximize,minimize:menu" or something.

Correct, solved, thanks.

---

### Post by Verbeck on 2010-11-16
my bad

---

### Post by stinkeye on 2010-11-16
Once you have the buttons where you want them,
in gconf-editor if you right click on the **button_layout** and choose 
**Set as Mandatory** the button layout won't change for old themes.
Right click and choose **Unset Key ** if you want to edit.

---

### Post by u-slayer on 2010-12-08
If anyone is searching for this, here is how to fix this in one command line:

```
gconftool-2 --set /apps/metacity/general/button_layout --type string “menu:minimize,maximize,close,spacer”
```

---

