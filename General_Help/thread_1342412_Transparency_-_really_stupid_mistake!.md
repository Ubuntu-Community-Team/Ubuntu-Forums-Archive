---
title: "Transparency - really stupid mistake!"
date: 2009-11-30
forum: General Help
---

### Post by zcacogp on 2009-11-30
Chaps, 

I hope you are sitting down. Yes? Good. 

I was just playing around with the transparency of windows in the "Opacity, brightness and saturation" section of Compiz (under 'accessibility'), and managed to make all of my windows transparent. Yes, fully transparent. Yes, by being careless with the slider. So, yes, I now can't see ANYTHING!

When you have finished laughing (which I am sure you are doing!), how can I solve this? I can open Compiz, but can't see anything in the window. Or in any other window. The machine is shut down now (this is being written on another machine), so I will (presumably) need to boot up to a terminal prompt, then open and edit the file with the 'opacity' settings in it. 

All suggestions welcome. (If you can stop sniggering for long enough to type ... )

Thanks, with much embarrassment ... 


Oli.

---

### Post by PariahVayne on 2009-11-30
[COLOR=White]x
[/COLOR]

---

### Post by nerdopolis on 2009-11-30
after you hit CTRL+ALT+F1, and before you run **metacity --replace** run ```
export DISPLAY=:0
``` first. then run **metacity --replace **then hit CTRL+ALT+F7.

---

### Post by ed-koala on 2009-11-30
Yes, I laughed. You have to.  But then I thought ... a warning should pop up before it allows you to do this.  You should submit a suggestion to Compiz to add a warning if anyone does what you just did, 'cause I can see me doing something just like that too.

---

### Post by peterballantyne on 2009-11-30
Yep - laughed like a drain - but I did exactly the same thing several days ago. Sat there staring at the lovely wallpaper feeling a complete idiot. After blindly "fishing" for the invisible setting for a while I gave up and thought, "Oh well, in Windows a reboot often clears problems!" And sure enough, a reboot seemed to bring everything back for me. One thing's for sure - we will both keep the slider off the zero end of the scale in future. I suspect a few folk will have been caught by this one. Hope it works out for you too. :lolflag:

---

### Post by zcacogp on 2009-12-01
Chaps, 

Thanks - that worked. Problem solved. All is now happy again. 

(Peterballantyne - glad I'm not the only one to make such a daft mistake 'round here!) 


Oli.

---

### Post by crm71 on 2009-12-01
Rather than settings nuke, if you were using the key binding defaults on that compiz plugin, alt and button4/5 (usually mapped to forward/back on mousewheel respectively) would raise and lower your opacity of the current window layered immediate under your mouse pointer.

Just for future reference. ;)

---

