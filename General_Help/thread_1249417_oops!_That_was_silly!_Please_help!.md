---
title: "oops! That was silly! Please help!"
date: 2009-08-25
forum: General Help
---

### Post by Aaron_Griffiths_92 on 2009-08-25
I was just installing a theme to ubuntu, and i was following the tutorial on transparency, but half way through changing it. I accidentally made everything transparent and lost everything. so now i cant see my task bar, right clicks or anything. How do i reset this?

---

### Post by howefield on 2009-08-25
> **Aaron_Griffiths_92 said:**
> How do i reset this?

Don't know, but it sounds a great laugh.

Try pressing alt + f2 to bring up a run dialogue, even if you can't see it, the focus should be on the text input field, so type metacity --replace and press enter.

You might then be able to fix whatever you've done.

---

### Post by Aaron_Griffiths_92 on 2009-08-25
That didnt work, just gave me an error, could you quote exactly what to type please?

---

### Post by howefield on 2009-08-25
metacity --replace

---

### Post by Aaron_Griffiths_92 on 2009-08-25
Thanks! I can see everything now... but everything that was supposed to be clear is now black...

*edit* what you told me to do broke a load of stuff, like all my effects, what do i do now?

---

### Post by drs305 on 2009-08-25
If you want to restore the default "Human" GTK2 theme:
```
gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "Human"
```

To change a metacity theme:
```
gconftool-2 --type string --set /apps/metacity/general/theme "name-of-metacity-theme"
```

Your effects may have disappeared because you were previously using compiz. To restore compiz:
```

compiz --replace

```

---

### Post by howefield on 2009-08-25
> **Aaron_Griffiths_92 said:**
> Thanks! I can see everything now... but everything that was supposed to be clear is now black...

*edit* what you told me to do broke a load of stuff, like all my effects, what do i do now?

Well, if you prefer it invisible, do the same again but this time type compiz --replace

The idea in getting you back to metacity was so that you can see what you are doing in order to reverse your cockups and then you can switch back on your effects.

---

### Post by Aaron_Griffiths_92 on 2009-08-25
> **howefield said:**
> metacity --replace

thanks! i figured out how to use what you said to fix it.

---

### Post by SlugSlug on 2009-08-25
> **Aaron_Griffiths_92 said:**
> 

  what do i do now?



step away from compiz

---

