---
title: "Is there a Dock program that works?"
date: 2010-08-19
forum: General Help
---

### Post by CoolJohnB on 2010-08-19
I have tried all the dock programs available in Software resources and everyone of them has 1 problem or another, for example I really like Docky but it blanks out the bottom 20% of the screen and although I can drag items from it, because of that I can't drag anything onto it.

The other 2 programs both make it difficult to add and remove from them.

Also with all 3 strange things happen, e.g. the windows applet at the top disappears or the screen might go "grey" for a long period of time.

So is there a docking program that works, "straight out of the box?"

---

### Post by KdotJ on 2010-08-19
I use cairo-dock (glx-dock I think it's called in repo?). It works fine for me, no problems. Lots of customisation and easy to add applets and launchers to it.

But I'm guessing that as you said you have tried the main ones, that you have tried Cairo-dock. 
What graphics card do you have? There are a few issues with certain applets with Cairo-dock running with an ATI card

---

### Post by Quackers on 2010-08-19
Cairo dock is good for me too :-)

---

### Post by bobcollard on 2010-08-19
Ditto, Cairo-Dock:

---

### Post by CoolJohnB on 2010-08-19
Ok I would like to try Cairo-Dock again but being new to Linux what's the easiest way of adding programs to it?  And removing the ones I don't want?

When I tried it before I noticed an option to browse for a program where do I look?

Any help would be much appreciated. Thanks in advance

---

### Post by jinba.ittai on 2010-08-19
I just stopped using AWN and started using Docky. Docky works fine for me. For now. But you guys suggest cairo dock is better?

---

### Post by drillerccg on 2010-08-19
> **jinba.ittai said:**
> I just stopped using AWN and started using Docky. Docky works fine for me. For now. But you guys suggest cairo dock is better?
I have Cairo installed on 6 identical laptops. Works great on 3 but buggy on the other 3. Frustrating at times. Main problem is the way the dock acts when you open windows (Auto hide or smart hide, etc). Also, Cairo has way too many options. Docky is simple but does not have enough options. Cairo is the best for now IMHO.

---

### Post by Quackers on 2010-08-19
CoolJohnB, right-click the dock - top option is cairo dock with a > then top option is configure. Add what you want from there.

---

### Post by Frogs Hair on 2010-08-19
I liked GLX dock and now I'm using the latest AWN ppa because of some new features they both work for me.

---

### Post by kerry_s on 2010-08-19
> for example I really like Docky but it blanks out the bottom 20%


you need to turn on compositing.
appearance-> visual effects, check "normal"
or
gconf-editor-> apps-> metacity-> general, check "compositing_manager"

---

### Post by bobcollard on 2010-08-19
To add application Icons either open an application from main menu and then right click it's Icon in the dock and click Make it a launcher or Open Application Finder and drag the icons into the Dock.  To Remove them, right click the Icon in the Dock and Remove This Launcher.

---

### Post by TNT1 on 2010-08-20
+1 for Cairo with open GL...

---

### Post by slooksterpsv on 2010-08-20
I have trouble with Cairo, I guess ATI and Cairo don't play nice lol, so I use Docky - but it does, like the previous person mentioned, need to have Composition enabled (install the drivers for your video card if there's any available in System -> Administration -> Hardware Drivers

---

### Post by mpranav007 on 2010-08-20
Try :p AWN - Avant Window Navigator!!!!

---

### Post by fabounet on 2010-08-20
@ATI cards owners:
use cairo-dock with "-c" option (that is to say, without opengl) if you have any problem (like invisible icons or visual artifacts).
You'll just loose the fancy 3D effects, but except that, the behavior shall be the same.
The recent cards and the recent drivers work pretty well though.

to install the latest version, there is a PPA (personnal repository); see [http://www.glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en]("http://www.glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en")
It's still a beta, but very stable and you can't miss the new features :-)

---

### Post by CoolJohnB on 2010-08-20
> **kerry_s said:**
> you need to turn on compositing.
appearance-> visual effects, check "normal"
or
gconf-editor-> apps-> metacity-> general, check "compositing_manager"


Thank you very much for your suggestion I can now use Docky although drag and drop doesn't work for some reason but by having the programs I want on it running when I first launched Docky and then right clicking I was able to pin them to it.

Guess I must have the wrong kind of graphics card for Cairo Dock as that still causes the screen to do strange things!

Appreciate very much all the help and suggestions, thanks.

---

