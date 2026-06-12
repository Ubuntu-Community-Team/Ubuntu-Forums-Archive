---
title: "annoying emerald!!!"
date: 2010-07-01
forum: General Help
---

### Post by SimplySimon... on 2010-07-01
So today i decided to install an emerald theme. Deciding i didn't like it i tried to switch back to my usual theme  (a gnome theme) so i pressed Alt-F2

```
metacity --replace
``` which restored my usual theme but my compiz settings weren't working and my awn window navigator had gone white instead of transparent so then i pressed Alt-F2

```
compiz --replace
```my compiz settings were working and the transparency was back although it applied the emerald theme, i tried un-installing emerald and trying the proses again but still no hope,

Reply asap, thanks

---

### Post by qamelian on 2010-07-01
You want to restart the gtk window decorator. Press alt-F2 and type:
```
gtk-window-decorator --replace
```

---

### Post by steveneddy on 2010-07-01
> **qamelian said:**
> You want to restart the gtk window decorator. Press alt-F2 and type:
```
gtk-window-decorator --replace
```

That is the correct answer.

This is one of the reasons most of us stopped using Emerald. Too buggy for me anyway.

---

### Post by SimplySimon... on 2010-07-02
Thanks sooo much!! :)

---

