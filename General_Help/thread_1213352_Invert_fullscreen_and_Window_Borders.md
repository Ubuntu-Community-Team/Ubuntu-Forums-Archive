---
title: "Invert fullscreen and Window Borders"
date: 2009-07-14
forum: General Help
---

### Post by wizardfait on 2009-07-14
I'm currently on a Gateway LT1004 with a broken screen. It was dropped by its previous owner, and now the screens colors are inverted. I am using Ubuntu 9.04, and using the "Negative" filter for Compiz to "fix" the problem. It works perfectly except for the desktop, anything in fullscreen, and the borders of windows.

As for the desktop, I found there was an "Exclude list" which included the desktop, so I removed that, and it fixed that issue. However, I now am sitting here with the borders of all windows still inverted (Blue-ish instead of orange, with black text, white shadows, and inverted icons) and the inability to go fullscreen without THAT reverting back to being inverted.

Is there a fix to make it invert EVERYTHING?

Yes, I do know the "easy" solution would be to replace the screen, but as I wish to not waste money when it's only a minor inconvenience, I'll try for a software solution first. :)

---

### Post by rainwalker on 2009-07-14
I've tried to figure out how to invert window borders as well, with no luck. I guess you could try messing around with it anyway, using values like "type=metacity" or stuff like that, but I haven't had any luck :?

---

### Post by wizardfait on 2009-07-15
> **rainwalker said:**
> I've tried to figure out how to invert window borders as well, with no luck. I guess you could try messing around with it anyway, using values like "type=metacity" or stuff like that, but I haven't had any luck :?

Thanks, but it already has set for which ones TO invert as "any"... So shouldn't that already include that?

---

### Post by rainwalker on 2009-07-15
> **wizardfait said:**
> Thanks, but it already has set for which ones TO invert as "any"... So shouldn't that already include that?

Yeah, that's why I haven't had any luck. Unfortunately, setting that value to "metacity" specifically doesn't help either.

I'll post back if I figure anything out, though.

---

### Post by wizardfait on 2009-07-15
> **rainwalker said:**
> Yeah, that's why I haven't had any luck. Unfortunately, setting that value to "metacity" specifically doesn't help either.

I'll post back if I figure anything out, though.

Okay, thank you. Just wondering, are you in the same predicament I am? Or just wanted to invert it for another reason?

---

### Post by rainwalker on 2009-07-15
> **wizardfait said:**
> Okay, thank you. Just wondering, are you in the same predicament I am? Or just wanted to invert it for another reason?

I'm not in the same predicament, but I use the invert feature to darken my screen at night. It used to include the window borders; I don't know what changed in Jaunty :?

---

### Post by wizardfait on 2009-07-15
> **rainwalker said:**
> I'm not in the same predicament, but I use the invert feature to darken my screen at night. It used to include the window borders; I don't know what changed in Jaunty :?

Maybe the window border "manager" has changed the way it draws to the screen.

In the "Other versions" that DID do the borders, did it also work in fullscreen?

---

### Post by CatKiller on 2009-07-15
Two thoughts. You could either pick/create/modify a theme so that it already has the colours inverted, so that they would look normal on your screen. You could possibly use gnome-color-chooser for this, to make it simpler. Or, if you have the requisite skills, you could get the source code for the neg plugin, and do what [this patch]("http://cgit.compiz.org/compiz/plugins/neg/commit/?id=27ddf0850304e5ff35366a70f78185462ee08074") did to the 0.8 branch, recompile and install. (As an alternative to this second suggestion, you could file a bug report asking that this patch be applied to the master branch, which might not happen, and would probably take a while if it did.)

With the fullscreen thing; there's an option for "Unredirect Fullscreen Windows" in the General section of CCSM. You'll probably want this unchecked, so that fullscreen windows still go through Compiz.

Actually, while I was researching the Negative plugin, I found this little titbit of information, so you can probably ignore everything that I wrote above:

> Workaround if unsupported *xcalib* can be used if the "Negative" filter is not supported by your hardware or driver. To invert the screen palette with *xcalib*: 

[LIST]
[*]xcalib -i -a
[/LIST]
Please note that *xcalib* is not part of Compiz Fusion.That does probably count as "a fix to make it invert EVERYTHING."

---

### Post by rainwalker on 2009-07-15
I think it's some change with compiz, actually. I don't think metacity changes that much, but compiz definitely is. I could be wrong though.
In Intrepid and before, everything but the desktop would invert, including window borders. It worked in fullscreen, only on specific windows, all that stuff. You can still do the specific windows, but I don't get why the window borders aren't included, especially since compiz composites the window decorations as well (with the "Window Decorations" plugin).

---

### Post by wizardfait on 2009-07-15
> **CatKiller said:**
> 
With the fullscreen thing; there's an option for "Unredirect Fullscreen Windows" in the General section of CCSM.

THANK YOU SO MUCH! I still need to try that x-whatever lib thing, but even if that doesn't work, this fullscreen fix is EXACTLY what I needed as a minimum! :D

---

### Post by CatKiller on 2009-07-15
> **wizardfait said:**
> but even if that doesn't work, this fullscreen fix is EXACTLY what I needed as a minimum! :D

Actually, I don't know for sure that it will work. It's just that having that setting checked means that fullscreen windows don't go through Compiz at all, for performance reasons, so not using that setting is a prerequisite for anything else working.

xcalib will definitely work, though, and will apply to everything. In case you were wondering what it does, this is what xcalib's man page says.

man xcalib:> 
 XCALIB(1)                           xcalib                           XCALIB(1)

NAME
       xcalib - Tiny monitor calibration loader for Xorg.As soon as I saw the suggestion, I remembered coming across this tool before. I use it to automatically calibrate my monitor to its hardware colour profile. The option that was given above is a simple inversion.

If it works and you want it to be applied automatically every time you log in you can put it in your ~/.xinitrc file. There's probably a way to make it work system-wide all the time, but I haven't looked into it.

---

### Post by wizardfait on 2009-07-16
So, if I do this... Do I DISABLE the compiz negative filter? And, will there be any performance difference between this and compiz?

---

### Post by CatKiller on 2009-07-16
> **wizardfait said:**
> So, if I do this... Do I DISABLE the compiz negative filter?

Yes, unless you want the windows to be negativised again.

> 
 And, will there be any performance difference between this and compiz?

I'd imagine that there isn't any performance penalty in using this method at all, and I haven't ever noticed any performance drop from using the Negative plugin over and above using Compiz itself. So no, not really. It's pretty negligible either way.

---

