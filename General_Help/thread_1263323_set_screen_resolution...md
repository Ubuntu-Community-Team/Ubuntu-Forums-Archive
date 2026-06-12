---
title: "set screen resolution..?"
date: 2009-09-10
forum: General Help
---

### Post by kikazaru on 2009-09-10
Ok, sorry for this noob question, but how can I set my screen resolution so that it stays set the next time I startup?

I can change the resolution to something sensible using xrandr or whatever, but it always boots up in super low res mode, and all the icons in the menubar get randomly jostled about so <violins lament my woe> I have to move them all back every time I boot up </violins>.


Ubuntu 9.04
Lenovo T400 laptop, ATI Radeon HD3400 ( using Catalyst 9.8 )

>uname -a
Linux laptop1 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

---

### Post by dcstar on 2009-09-10
> **kikazaru said:**
> Ok, sorry for this noob question, but how can I set my screen resolution so that it stays set the next time I startup?
.........

System-Preferences-Display.

---

### Post by earthpigg on 2009-09-10
and reason you aren't using system -> preferences -> display?

---

### Post by kikazaru on 2009-09-10
"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

Pressing "Yes" gives me the Catalyst configuration tool. I can change the resolution with this tool, but it is not retained when I restart.

---

### Post by earthpigg on 2009-09-10
> **kikazaru said:**
> Pressing "Yes" gives me the Catalyst configuration tool. I can change the resolution with this tool, but it is not retained when I restart.

have you tried running catalyst as root?

i would assume/guess it is 'sudo catalyst'... but i have never used an ATI card with linux.

we have the same problem with nvidia, though. if you point/click in the menus to the nvidia-settings app, your settings aren't saved.

if you run 'sudo nvidia-settings' then your settings are saved.

---

### Post by kikazaru on 2009-09-11
Ah, that sounds like it has potential... I'll try it and report back.

Thanks!

---

### Post by sleepitoff on 2009-09-11
You could just create a script to be read at login that sets your resolution for you automatically...  

Open a text editor, add the lines... 

xrandr --output VGA --mode 1280x800 --pos 0x0 --rotate normal 

save as whateveryoulike.sh and add it to your start up menu list. 

obviously changing the resolution to whatever yours is or whatever else you feel fit to from my example.

---

### Post by kikazaru on 2009-09-11
Thanks for the suggestion. This occurred to me. In fact I already made a couple of easy key-bindings to switch resolution with xrandr because I often use a projector which does not support the full resolution of my screen. So it's only a minor irritation to switch it manually when I log in, and of course I could automate it as you suggest.

The main thing that's bugging me is that when I log in it drops to a super low resolution and all the icons in my menubar get mixed about and reordered. So I'd like to avoid ever going into that graphics mode!

---

