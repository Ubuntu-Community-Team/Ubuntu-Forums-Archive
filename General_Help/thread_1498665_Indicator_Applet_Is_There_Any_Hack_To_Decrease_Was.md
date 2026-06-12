---
title: "Indicator Applet: Is There Any Hack To Decrease Wasteful Default Icon Spacing?"
date: 2010-06-01
forum: General Help
---

### Post by OzzyFrank on 2010-06-01
Pretty much the only reason I am not using **Indicator Applet **is because of this **[COLOR="Red"]horridly-large icon spacing[/COLOR]** between its entries. Not being fussy here - besides all the launchers on my panel, I have the ever-growing system tray trying to claim its territory. Quite literally, every pixel counts, I'm afraid.

Now, I've come across some clever hacks, for removing default entries, and for adding things like Thunderbird to the mail notifier. The one thing I haven't seen addressed yet is this issue of icon spacing, yet I'm thinking there must be a config file somewhere telling it to space icons a certain amount, and I gather it can be edited. Any ideas?

---

### Post by dino99 on 2010-06-01
i'm able to move these icons as i want by right clicking on panel

---

### Post by SoFl W on 2010-06-01
Right click and move on the icon doesn't work?  How about right clicking on it and adjusting variables in the properties tab?

---

### Post by OzzyFrank on 2010-06-01
Are you talking about the icons within the Indicator Applet, or just launchers on the panel? The notification icons in the Indicator Applet are set a certain distance apart, and you cannot move individual ones (right-clicking and choosing *Move* moves the whole Indicator Applet along the panel, at least from where I'm sitting).

EDIT: OK, just saw you mention the Properties tab, so you're definitely talking about launchers, not Indicator Applet.

---

### Post by SoFl W on 2010-06-01
I did a quick search and you are not the only one complaining about this.  (BTW this thread is already the second  result on google) 
Have you thought about adding a second panel if your first panel is too crowded?

---

### Post by OzzyFrank on 2010-06-01
Hehe, nah, then I have too many panels, hehe! I keep it manageable, but when the system tray fills up a bit it starts pushing the launchers together. I try to put things I don't always use in Drawers, which are a great idea, and I have more in those drawers than visible on the panel. The other thing is I have spaces between groups of icons, separated by tasks/uses, so it's not all one big mess, which is another reason I need the real estate!

---

### Post by kerry_s on 2010-06-01
for the volume you can use the old 1 "**gnome-volume-control-applet**"
the programs you just need to turn the notification icons back on.
the session indicator, do you really even need that you can log out from the menu.
the desktop is a big open space, you could put a lot there.

there's lots of options you just need to try different things.

i really don't use a lot of things, so i went with panels & slab menu, i mostly use the panels though, i haven't open the menu in a couple of days. i had drawers but found them annoying, even with the auto close turned off.

i don't have nothing on the desktop, heres a pic.

---

### Post by SoFl W on 2010-06-01
> **OzzyFrank said:**
> Hehe, nah, then I have too many panels, hehe! I keep it manageable, but when the system tray fills up a bit it starts pushing the launchers together. I try to put things I don't always use in Drawers, which are a great idea, and I have more in those drawers than visible on the panel. The other thing is I have spaces between groups of icons, separated by tasks/uses, so it's not all one big mess, which is another reason I need the real estate!

Have you tried using the workplace switcher?  Have different applications open in different workplaces, it keeps things cleaner.  I have Thunderbird in one, FireFox in another, gimp in a third, etc  This keeps the system tray cleaned up.

---

### Post by OzzyFrank on 2010-06-01
Thanks for your time guys, but I don't actually have any problems, and my panel is pretty much as I want it. I do in fact use the old volume button, only have the small shutdown button on the end, and happily use drawers (love em!) for all my other launchers.

I'm just trying to get the hack for how to edit the spacing between icons Indicator Applet displays from someone that knows it. Purely a curiosity thing, but will help those that actually want to use Indicator Applet (I don't, but then again might be persuaded if I can get this answer, as I already know how to remove things I don't want there).

As for switching workplaces, I never actually got into that, since as far as I could see, desktop icons and the panels were shared. That would be awesome if every desktop had a different panel... I would definitely get into it then.

So thanks for all your cool suggestions, but I just want this answer, since it has to be out there. I might even start digging in config files I haven't looked in yet and see if I find anything, when I have more time. Cheers.

---

### Post by erlguta on 2010-06-12
I have the same problem. I am surprised that there is not one bug open about this.
¿Is there any bug filed about this in launchpad?

---

### Post by erlguta on 2010-06-12
Yes, there is. 
[https://bugs.launchpad.net/indicator-application/+bug/527267](https://bugs.launchpad.net/indicator-application/+bug/527267)

And and surprisingly it is not considered a bug...

---

### Post by OzzyFrank on 2010-06-12
Surprised? I was just about to comment it ISN'T a bug, but a rather silly design flaw. I think bugs come more under "coding error". That's why I never filed a bug report on this.

---

### Post by mikefreeman on 2010-11-30
Someone posted a patched version of the Indicator Applet in a bug report about the icon spacing, and it was put into a PPA. If interested, add this to your Software Sources: ppa:m0sia

From there you just upgrade the indicator applet in Synaptic, Update Manager, APT, or wherever.

As always, use unknown/untrusted software sources at your own risk. I can tell you that it works on my computer. It's not perfect, as it's still not as tightly packed together as the Notification Area icons, but it does reduce the spacing between the icons in the Indicator Applet by quite a lot.

---

### Post by redman5087 on 2011-02-06
> **mikefreeman said:**
> Someone posted a patched version of the Indicator Applet in a bug report about the icon spacing, and it was put into a PPA. If interested, add this to your Software Sources: ppa:m0sia

From there you just upgrade the indicator applet in Synaptic, Update Manager, APT, or wherever.

As always, use unknown/untrusted software sources at your own risk. I can tell you that it works on my computer. It's not perfect, as it's still not as tightly packed together as the Notification Area icons, but it does reduce the spacing between the icons in the Indicator Applet by quite a lot.

Thanks

---

### Post by ZeroFossilFuel on 2011-04-20
I have had to refer back to this thread at least a half dozen times to "Fix" this irritation the Ubuntu team seems to think is not a bug. If hoards of people hate it and there's no convenient way to change the settings, IT'S A BUG!!!

Thank you for pointing out this PPA. Works great.

Z

---

