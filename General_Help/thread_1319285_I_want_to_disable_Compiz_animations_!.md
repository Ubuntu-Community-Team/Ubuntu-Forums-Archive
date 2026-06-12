---
title: "I want to disable Compiz animations !"
date: 2009-11-08
forum: General Help
---

### Post by abelthorne on 2009-11-08
Hello,
I've just installed Karmic on my laptop to replace Jaunty.
One of the first thing I did was to install CCSM in order to tune Compiz as I need it. I encountered my first problem: I can't turn animations off as I used to do since Gutsy.

While searching for a fix to what I consider a bug, I found the following subject: [http://ubuntuforums.org/showthread.php?t=1280562](http://ubuntuforums.org/showthread.php?t=1280562)

Can someone confirm that I did not misunderstood (english isn't my primary language) and that animations can't be disabled on purpose? If so that just sucks and I won't use Compiz while it is the case (these animations really bother me, I used Compiz mainly to have composited display and for usability as I could browse through virtual desktops with the mouse wheel - BTW it doesn't work anymore: is it another choice from the devs?).

---

### Post by MelDJ on 2009-11-08
install compizconfig-settings-manager from synaptic.
it will come under system-preferences.
there you can edit  compiz configurations

---

### Post by abelthorne on 2009-11-08
I've already installed CCSM (CompizConfig Setting Manager). My problem is that the Animations plugins can't be disabled. See the link I've put in my message.

---

### Post by stinkeye on 2009-11-08
> **abelthorne said:**
> Hello,
I've just installed Karmic on my laptop to replace Jaunty.
One of the first thing I did was to install CCSM in order to tune Compiz as I need it. I encountered my first problem: I can't turn animations off as I used to do since Gutsy.

While searching for a fix to what I consider a bug, I found the following subject: [http://ubuntuforums.org/showthread.php?t=1280562](http://ubuntuforums.org/showthread.php?t=1280562)

Can someone confirm that I did not misunderstood (english isn't my primary language) and that animations can't be disabled on purpose? If so that just sucks and I won't use Compiz while it is the case (these animations really bother me, I used Compiz mainly to have composited display and for usability as I could browse through virtual desktops with the mouse wheel - BTW it doesn't work anymore: is it another choice from the devs?).
Cant you just just remove the animation effects from the ones you don't want.Mousewheel desktop switching is available in the viewport switcher.
Sooky LaLa's.

---

### Post by abelthorne on 2009-11-08
> **stinkeye said:**
> Cant you just just remove the animation effects from the ones you don't want.
What do you mean?
My problem is that if I uncheck the Animations plugin, it is set back automatically a few secondes later. From the other thread, it seems that this behaviour is wanted by the devs and that the Animations plugin is now mandatory. But I'm not sure to understand why.

> Mousewheel desktop switching is available in the viewport switcher.
Thanks, but I don't understand how to set the wheel. I can bind keys to "next" and "previous desktop" but I can only choose buttons 1 to 9 (with optional keys). I don't see the wheel in the list.

---

### Post by stinkeye on 2009-11-08
> **abelthorne said:**
> What do you mean?
My problem is that if I uncheck the Animations plugin, it is set back automatically a few secondes later. From the other thread, it seems that this behaviour is wanted by the devs and that the Animations plugin is now mandatory. But I'm not sure to understand why.


Thanks, but I don't understand how to set the wheel. I can bind keys to "next" and "previous desktop" but I can only choose buttons 1 to 9 (with optional keys). I don't see the wheel in the list.
Try setting the animation effect to none.
On my mouse buttons 4 & 5 are the wheel.

---

### Post by abelthorne on 2009-11-08
Ok, it works. But removing the settings while keeping the plugin active kinda looks like a hack to me. :/
If someone knows of a way do completely disable the Animation plugin, I'd be glad.

---

### Post by stinkeye on 2009-11-08
](*,)

---

### Post by catco_designs on 2009-11-08
Have you thought of simply changing your appearance preferences to normal

---

### Post by abelthorne on 2009-11-08
> **catco_designs said:**
> Have you thought of simply changing your appearance preferences to normal
Yes.

What I'd like to know is:
- it seems that during the development of Karmic, it has been decided that Compiz Animations plugin would not be deactivable: is it the case or am I misunderstanding this point?
- is there a way to bypass this limitation, i.e. let me uncheck the Animations plugin in CCSM without it checking automatically back? maybe a gconf setting, an update for Compiz or a patch?
- are there plans to revert to the previous behaviour in the future? Forcing the user to use a plugin he doesn't want seems really stupid to me

---

### Post by Druke on 2009-11-08
> - it seems that during the development of Karmic, it has been decided that Compiz Animations plugin would not be deactivable: is it the case or am I misunderstanding this point?

[s]I think you may be misunderstanding... I can right click on the desktop and under the visual effects tab, click NONE. Turns everything off.[/s] Read my next post first.

---

### Post by nothingspecial on 2009-11-08
This doesn`t really help you but I thought I`d pipe in.

The same behaviour is apparent with the window decoration plugin. I don`t like my windows decorated. I solved it by deleting /usr/bin/compiz-decorator (or whatever it was called - can`t check coz it`s gone)

I can`t find a similar thing for the animations though.

---

### Post by Druke on 2009-11-08
oooooohhhhhhhh I understand, sorry for my dumb post above. Turning off the animations plugin in compiz isn't really a hack at all.

The animations are an extension of compiz, so if you want things like the fancy window decorators, desktop navigation and such, you simply disable the animations extension.

If you want none of the compiz stuff running, you can simply disable it like I said in my previous post.

---

### Post by nothingspecial on 2009-11-08
I have no idea if this will work but try going into the gconf-editor and navigate apps > compiz > animations.

Then untick (uncheck) every box and reset every number to zero.

Although that won`t actually disable the plugins it may turn each individual one off.

---

### Post by nothingspecial on 2009-11-08
or you could try removing ~/.gconf/apps/compiz/plugins/animation

Don`t know if that would mess things up though.

---

### Post by catco_designs on 2009-11-08
I really dont get what you are trying to achieve 
the so called hack is how you adjust it
> I don't really know what a hack is though could someone PLEASE explain the term

---

### Post by Druke on 2009-11-08
I think we're mainly seeing a language barrier, he has everything running correctly, just doesn't understand why methinks.

---

### Post by nothingspecial on 2009-11-08
I don`t give a monkeys about compiz or any fancy stuff it does. All I know is it used to be the easiest way to take those silly window borders with - and x and soforth displayed on them.

In Karmic, compiz-config-settings manager won`t let you. Every time you uncheck (untick) the box it goes and puts it back in. I`m assuming the behaviour is the same for the animations plugin.

---

### Post by abelthorne on 2009-11-08
> **Druke said:**
> oooooohhhhhhhh I understand, sorry for my dumb post above. Turning off the animations plugin in compiz isn't really a hack at all.
I think there's a misunderstanding here. The problem is that I can't turn it off. If unchecked in CCSM, the checkmark comes back automatically. This was not the case before Karmic and the Animations plugin could be disabled.

I consider the solution given above a hack because I find it quite "ugly" to delete preferences for a plugin (removing all the effets in that case) rather than being able to disable the plugin itself. Ok, it works but if I want animations tomorrow, I have to set back all the effects and remove them when I don't want the animations anymore.

What I don't understand is why Animation (and maybe others) can't be disabled anymore. To me it looks like a bug but from the other thread, it seems that it's a "feature".

Again, this behaviour appeared in Karmic. If you're running Jaunty or older and can't see what my problem is, it's normal. :)
But if you are running Karmic and can disable the Animations plugin in CCSM, there must be a problem somewhere on my system.

I'll try the Gconf key to see if disabling Animations there works. Or if it breaks Compiz.

EDIT : I can confirm the same behaviour with the Windows Decoration plugin : can't turn it off either. Why the hack can't we decide how we want to setup Compiz anymore ?

---

### Post by issih on 2009-11-08
Read the thread that the OP posted...it contains the work around:

Read the very first post on this page.

[http://ubuntuforums.org/showthread.php?t=1280562&page=2](http://ubuntuforums.org/showthread.php?t=1280562&page=2)

It details exactly how to fix it. The thread also details why it is forced to enabled too....its quite interesting.

---

### Post by catco_designs on 2009-11-08
> **issih said:**
> Read the thread that the OP posted...it contains the work around:

Read the very first post on this page.

[http://ubuntuforums.org/showthread.php?t=1280562&page=2](http://ubuntuforums.org/showthread.php?t=1280562&page=2)

It details exactly how to fix it. The thread also details why it is forced to enabled too....its quite interesting.

> I can confirm the same behaviour with the Windows Decoration plugin : can't turn it off either. Why the hack can't we decide how we want to setup Compiz anymoreThis is simply because windows decorations and animations work together

---

