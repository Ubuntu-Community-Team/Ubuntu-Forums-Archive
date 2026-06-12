---
title: "Strange Min-Max-Close buttons"
date: 2010-08-17
forum: General Help
---

### Post by DeMus on 2010-08-17
Since a few days I have Min-Max-Close buttons which don't belong to the theme I have chosen. It doesn't matter which Theme I choose, these buttons stay the same and they look ugly.
How can this happen and what can I do to get the buttons belonging to the Theme I have chosen?

---

### Post by DeMus on 2010-08-17
Bump!

---

### Post by sydbat on 2010-08-17
> **DeMus said:**
> Since a few days I have Min-Max-Close buttons which don't belong to the theme I have chosen. It doesn't matter which Theme I choose, these buttons stay the same and they look ugly.
How can this happen and what can I do to get the buttons belonging to the Theme I have chosen?At some time in the past, did you "customize" a default theme? I wonder if one of the other settings, like "Icons" might need to be changed to your new theme. Other than that, I have no idea.

---

### Post by Cavsfan on 2010-08-17
I have no idea if this will help, but sometimes my buttons disappear and the top of the windows go dark.
I found that I can go to my Cairo Dock Compiz icon and click on Reload WM and that fixes it for me every time.
HTH

---

### Post by DeMus on 2010-08-17
> **sydbat said:**
> At some time in the past, did you "customize" a default theme? I wonder if one of the other settings, like "Icons" might need to be changed to your new theme. Other than that, I have no idea.

I have tried other themes and no matter which one, the icons in the top right corner stay the same. I can also customize themes, also that doesn't help.
To answer your question, I am sure I have done something but I have no idea what and where.

---

### Post by DeMus on 2010-08-17
> **Cavsfan said:**
> I have no idea if this will help, but sometimes my buttons disappear and the top of the windows go dark.
I found that I can go to my Cairo Dock Compiz icon and click on Reload WM and that fixes it for me every time.
HTH

Thanks for the advice, but reloading the WM did not help me. When I change the WM the buttons change, but then Compiz doesn't work anymore. So I have to choose Compiz as WM.

---

### Post by DeMus on 2010-08-17
Have a look at the attached picture to see the buttons I currently have, and don't want.

---

### Post by TheWeakSleep on 2010-08-17
Are you using emerald themes by any chance?

---

### Post by Cavsfan on 2010-08-17
> **DeMus said:**
> Thanks for the advice, but reloading the WM did not help me. When I change the WM the buttons change, but then Compiz doesn't work anymore. So I have to choose Compiz as WM.

I am using Emerald manager and I am not sure what put the icon there, but I meant I click on an Icon called 
**Reload WM** and it is the one at the top right of the 5 in the Compiz icon in the dock.
I do know what you mean about how complicated all of this is! I am learning more about it all the time! :D

---

### Post by Cavsfan on 2010-08-17
If you aren't using the Emerald Manager, maybe that would fix your problem.
I have not touched any settings on it because I like them the way they are,

When I click on Emerald manager, it takes several seconds for it to open up 
and then when I click on Edit Themes, I am using **vrunner (0.2)** just in case this info is beneficial.

---

### Post by TheWeakSleep on 2010-08-17
To me, it looks like an emerald theme that has the option "use pixmap buttons" unchecked. If you are using emerald themes for your window borders, under emerald theme manager, try clicking "edit themes," click the tab for "buttons" and check the box that has the option for using pixmap buttons. That might work :)

Edit: @Cavsfan, that sounds like the compiz-fusion icon to me

---

### Post by DeMus on 2010-08-18
> **TheWeakSleep said:**
> To me, it looks like an emerald theme that has the option "use pixmap buttons" unchecked. If you are using emerald themes for your window borders, under emerald theme manager, try clicking "edit themes," click the tab for "buttons" and check the box that has the option for using pixmap buttons. That might work :)

Edit: @Cavsfan, that sounds like the compiz-fusion icon to me

Will have a look into it this evening when I am home. I am at work now using this dreadfull W*****s system.
Thanks for the help.

---

### Post by mcduck on 2010-08-18
If you *aren't* using Emerald, then open gconf-editor and make sure the apps/gwd/use_metacity_theme -key is enabled.

If that's disabled GWD will fall back to the default Compiz theme instead of your Metacity theme.

---

### Post by DeMus on 2010-08-18
> **mcduck said:**
> If you *aren't* using Emerald, then open gconf-editor and make sure the apps/gwd/use_metacity_theme -key is enabled.

If that's disabled GWD will fall back to the default Compiz theme instead of your Metacity theme.

You're the man. Thank you so much. Well, all others thank you also for giving advices, but McDuck is the winner. I have no idea why this tick-box was not enabled. To my knowledge I have never changed anything in app/gwd/ in config-editor. 
Anyway, this problem is solved and you have made me very happy. Thanks again.

---

### Post by Cavsfan on 2010-08-18
> **DeMus said:**
> You're the man. Thank you so much. Well, all others thank you also for giving advices, but McDuck is the winner. I have no idea why this tick-box was not enabled. To my knowledge I have never changed anything in app/gwd/ in config-editor. 
Anyway, this problem is solved and you have made me very happy. Thanks again.

Glad McDuck figured it out for you! I know all of this stuff is very complicated at least to me! 
And I am afraid to touch any of it because I really like the way it currently works!
Sure enough if I messed with anything I would "break" it. :)

---

