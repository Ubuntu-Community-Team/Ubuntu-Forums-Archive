---
title: "I'm new...HELP!"
date: 2009-11-05
forum: General Help
---

### Post by LSUSOBEAST on 2009-11-05
I just made the switch to Ubuntu!!!!  But I have encountered a few problems.

On my windows, there are no minimize, maximize, or close buttons.  The only way for me to complete these commands is to right click the tab at the bottom.

Also, I cannot simply grab the window and move it by clicking on the title bar.  Why?!?!

Please help!!!!!

Dumb it down a little since I am still getting used to this!!

---

### Post by mdurham on 2009-11-05
You can try System->Preferences->Appearance select the 'Visual effects' TAB and then select 'none' and see what happens!
Cheers, Mike

---

### Post by kixome on 2009-11-05
if you went with the newst ubuntu, then you made your first mistake, either go with 8.04 or 9.04, never go with the X.10 versions as they are ten times as buggy as the .04 versions. and .04 versions end up stable whereas it has been my experience that .10 versions never do!

---

### Post by SlugSlug on 2009-11-05
> **kixome said:**
> if you went with the newst ubuntu, then you made your first mistake, either go with 8.04 or 9.04, never go with the X.10 versions as they are ten times as buggy as the .04 versions. and .04 versions end up stable whereas it has been my experience that .10 versions never do!


is this true? whats the diff between .10 and .04's

---

### Post by The Funkbomb on 2009-11-05
No, that's not true.  8.10 was a beautiful piece of software.

9.10 is buggy because it was released about a week ago.  Ubuntu's numbering system works like this.

The first number is the year it was released.  9 as in 2009.  After the decimal, it's the month.  9.04 is April 2009.  9.10 is October 2009.

Sorry, I can't help with your original problem.

---

### Post by kiridude on 2009-11-05
That's pretty weird. I would suggest trying a new install.

---

### Post by P4man on 2009-11-05
Lets not blame every issue anyone encounters on 9.10. Yes some people have issues with it, but for most it works fine.

LSUSOBEAST, you are not running a windows decorator. have you tried enabling compiz ?

A quick fix is pressing alt f2 and typing

```
metacity --replace
```

The real solution depends what you did earlier, but Ill wait for more info on that.

BTW, you can move any window, even one without borders by holding down the ALT key. Then you can drag the window even from the center.

---

### Post by nothingspecial on 2009-11-05
Are you using compiz?

Try typing ```
metacity --replace
```

or 

sudo apt-get install ```
compizconfig-settings-manager
```

Then in the menu system > preferences > compiz(whatever it says) and make sure the window decoration button is cheched (ticked)

---

