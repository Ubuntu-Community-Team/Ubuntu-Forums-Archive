---
title: "I cant enable extra effect in 10.10"
date: 2011-02-13
forum: General Help
---

### Post by ravij96 on 2011-02-13
Hi I'm running 10.10 and whenever i click on extra under visual effects in Appearance I'll get the keep settings dialogue box, but then the effects don't enable and if i go back to the page the effects is back on none. I am very lost and would be happy for answers.

My grpahics card is a ATI Radeon HD 3200 graphics card.

---

### Post by VinDSL on 2011-02-13
> **ravij96 said:**
> Hi I'm running 10.10 and whenever i click on extra under visual effects in Appearance I'll get the keep settings dialogue box, but then the effects don't enable and if i go back to the page the effects is back on none. [...]
Have you installed the compiz-fusion-plugins-extra package?

I've forgotten to do that, many times, and the results are as you described...  :D

---

### Post by Randymanme on 2011-02-13
Have you downloaded and installed a proprietary driver for your graphics card?  Go to Menu>System>Administration and click on Additional Drivers if you haven't updated your graphics card driver yet.

---

### Post by ravij96 on 2011-02-13
> **VinDSL said:**
> Have you installed the compiz-fusion-plugins-extra package?

I've forgotten to do that, many times, and the results are as you described...  :grin:
No, I have not installed this where do I get it from i can not find it in the software center?

---

### Post by ravij96 on 2011-02-13
OK I have downloaded  compiz-fusion-plugins-extra package and it did not fix my problems. I have also updated my graphics card and it didn't fix my problems either. Also before i had this problem my title bar on windows disappeared and i fixed that by putting metacity as a start up program. I just wanted to add that in case it helps or anything.

---

### Post by Dustin2128 on 2011-02-13
what kind of gfx chip are you using, nvidia, ATI, intel? Some cards may not be able to handle compiz (very very old ones) and most need proprietary drivers installed as noted above.

---

### Post by HiImTye on 2011-02-14
try installing the compiz icon
```
sudo apt-get install fusion-icon
```
then try switching to compiz, manually using the icon (note: you will need to launch the icon from applications and if you want it to run at boot you will need to add it to your startup applications)

---

### Post by VinDSL on 2011-02-14
> **ravij96 said:**
> OK I have downloaded  compiz-fusion-plugins-extra package and it did not fix my problems. I have also updated my graphics card and it didn't fix my problems either. Also before i had this problem my title bar on windows disappeared and i fixed that by putting metacity as a start up program. I just wanted to add that in case it helps or anything.So far, so good...

OK... once I have the compiz-fusion-plugins-extra package installed, I forget about clicking the visual effects in Appearance.

From here on out, I use CompizConfig Settings Manager (CCSM) in System -> Preferences.

I keep a 'cheat sheet' around here, with all my Compiz settings.  I've used Compiz long enough that I know what I like, but it isn't relegated to memory.  Too many settings to remember, off the top of my head.


Here's how the Compiz looks on my ol' dog (as I type)...

[INDENT][IMG]http://vindsl.com/images/vindsl-compiz-snappie(600x480).png[/IMG][/INDENT]


Anyway, once you get everything setup in CCSM, then the radial in Appearance should indicate that extra visual effects are being used.  

Do all of your changes in CCSM, not in the Appearance window.  ;)

If things are not 'sticking' in CCSM, then you might have a compatibility issue with your graphic card.  Not all cards will do all things, in Compiz, but playing around in CCSM will give you a fighting chance.

Also... DO NOT use Metacity as your compositor!!!  It's ok to use Metacity for window decorations, themes, et cetera, but you can only run one compostor at a time - either Compiz, or Metacity - but NOT both, at the same time.

Hang in there!  You'll get it...

---

### Post by mcduck on 2011-02-14
> **ravij96 said:**
> Also before i had this problem my title bar on windows disappeared and i fixed that by putting metacity as a start up program.

That's your problem there... :)

If you are using Metacity, you aren't using Compiz (only one window manager can run at a time). And Compiz is the one that¨s able to do all the nice effects.

(The Visual Effects -option in the Appearance dialog switches between running Metacity the "none"-option) and two different pre-configured Compiz setups)

---

### Post by ravij96 on 2011-02-14
Ok thanks guys Ill try this when I get home.

---

### Post by ravij96 on 2011-02-14
> **Dustin2128 said:**
> what kind of gfx chip are you using, nvidia, ATI, intel? Some cards may not be able to handle compiz (very very old ones) and most need proprietary drivers installed as noted above.
Also I am using an ATI and it use to work I am not home right now and will try the fixes when I get home

---

### Post by VinDSL on 2011-02-14
An easy way to see (and control) if Metacity compositing is enabled is to use a proggie called Ubuntu Tweak.


[INDENT][IMG]http://vindsl.com/images/vindsl-compiz-snappie(2).png[/IMG][/INDENT]


All you have to do is check/uncheck the box at the bottom.  ;)

---

### Post by ravij96 on 2011-02-14
Ok so I switched to Compiz but still the same problem so then I installed the compiz icon and if i switch to compiz I can put my graphics to what ever i want but the title bar missing.  Also, the title bar is only missing in extra and normal

---

### Post by ravij96 on 2011-02-14
Also I ran SKIP_CHECKS=yes compiz and this came uo

libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
kde-window-decorator(2641) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen"
kde4-window-decorator: Could not enable decorations on display ":0.0"
kde-window-decorator(2639) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen"
kde4-window-decorator: Could not enable decorations on display ":0.0"

---

### Post by ravij96 on 2011-02-14
I fixed the problem by reinstalling thanks for the help.

---

### Post by VinDSL on 2011-02-15
> **ravij96 said:**
> I fixed the problem by reinstalling thanks for the help.
Good deal!

---

### Post by ravij96 on 2011-02-15
> **VinDSL said:**
> Good deal!
Yep all though not the best option to fix the problem because of the fact that you can lose data after the reinstall I only had Ubuntu for 2 days. So it will be easy to recover everything.

---

### Post by VinDSL on 2011-02-15
> **ravij96 said:**
> Yep all though not the best option [...] I only had Ubuntu for 2 days.
Oh!  I thought you meant you reinstalled Compiz - not the whole enchilada. Yikes!

Sometimes Compiz gets hopelessly jacked up, and the only option is to reinstall Compiz.

That's why I keep a "cheat sheet" handy, with all of my favorite Compiz settings. :D  

Reinstalling is very simple, using the Synaptic (Package Manager).

Whenever you click on an installed package in Synaptic, it gives you several options:
[INDENT][LIST]
[*]Mark for Reinstallation
[*]Mark for Removal
[*]Mark for Complete Removal
[/LIST][/INDENT]

Anyway, next time Compiz pukes -- and it will -- just reinstall Compiz. ;)

---

### Post by ravij96 on 2011-02-15
> **VinDSL said:**
> Oh!  I thought you meant you reinstalled Compiz - not the whole enchilada. Yikes!

Sometimes Compiz gets hopelessly jacked up, and the only option is to reinstall Compiz.

That's why I keep a "cheat sheet" handy, with all of my favorite Compiz settings. :D  

Reinstalling is very simple, using the Synaptic (Package Manager).

Whenever you click on an installed package in Synaptic, it gives you several options:[INDENT]
[LIST]
[*]Mark for Reinstallation
[*]Mark for Removal
[*]Mark for Complete Removal
[/LIST]
[/INDENT]Anyway, next time Compiz pukes -- and it will -- just reinstall Compiz. ;)
Wow nice to know thanks.  Hey my question is my partition use to be 29.1gb now its 27 gb what happen? Should I kind of wanted to ask here since starting a new thread might be pointless.

---

