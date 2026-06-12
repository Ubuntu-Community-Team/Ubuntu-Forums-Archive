---
title: "Keyboard indicator is useless on 10.10. How to revert?"
date: 2010-10-11
forum: General Help
---

### Post by yesint on 2010-10-11
I've just upgraded to 10.10. Everything is smooth and there are no problems at all BUT... new keyboard indicator in the notification area shows the same dumb keyboard icon all the time instead of layout abbreviation "EN", "RU" etc. New indicator does not indicate anything in fact!
Is there any way to reset old behavior?

---

### Post by margitajemrtva on 2010-10-12
I also think that the new keyboard layout indicator is useless.
anyone have idea how to revert?

---

### Post by copyhold on 2010-10-14
Faced the same issue. Solved by removing and adding back to panel:
* indicator
* indicator session
* notification

I'm not sure wich one exactly. Seems one of them had not enough space for showing current layout.
Although I agree - KB icon is useless.
How to remove?

---

### Post by monkeyKata on 2010-10-14
+1 for sure.

And, too, it seems now you can no longer change between layouts in one click, but rather must choose the layout you want after bringing down the menu.  Sure it's a slight difference, but it just makes this simple task a little slower when it doesn't need to be, in my opinion.  

It would be nice to have options to both get rid of the icon and enable a single-click switch like before, maybe with a right-click bringing down the menu.

---

### Post by margitajemrtva on 2010-10-14
i've added the "Indicator Applet" to the panel, and now i can see the keyboard layout, but i also see that totally useless keyboard icon, volume and mail icon which both i don't need.
is there a way to remove these from "indicator applet"?

someone reported a "Better keyboard layout distinction in keyboard indicator" as a bug:
[https://bugs.launchpad.net/indicator-applet/+bug/660269](https://bugs.launchpad.net/indicator-applet/+bug/660269)

---

### Post by monkeyKata on 2010-10-14
This post helped me to get rid of the mail icon:

[http://ubuntuforums.org/showthread.php?t=1470786&highlight=indicator+applet+mail+icon](http://ubuntuforums.org/showthread.php?t=1470786&highlight=indicator+applet+mail+icon)

---

### Post by ENigma885 on 2010-10-20
This idea is really nice. [http://gnome-look.org/content/show.php/Language+Flags+for+Faenza+and+Elementary?content=133726](http://gnome-look.org/content/show.php/Language+Flags+for+Faenza+and+Elementary?content=133726)

You will get something like:
[IMG]http://img409.imageshack.us/img409/5962/1337261.png[/IMG]

**[COLOR="Red"]Still[/COLOR], two mouse clicks are needed to switch the keyboard layout. Better is to add a keyboard shortcut from *"Keyboard Preferences>>Layouts>>Options>>Key(s) to change layout"*. Personally, I use ALT+Shift.

---

### Post by gesy on 2010-10-30
Marjitajemrtva (Ouf!): it works. Thanks.

But the layout applet doesn't show the right layout if we change it with a shortcut. It's a very bad issue.

---

### Post by Luffield on 2010-11-29
Here's a bug with a suggestion to assign the scroll wheel to quickly change layouts. It seems to be pretty much abandoned, though :-\
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/624689](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/624689)

---

### Post by Claus7 on 2011-12-17
Hello,

I was struggling to show flag icons with the ubuntu maverick's keyboard indicator applet to no avail.

*The solution*:gconf-editor (after Alt+F2) and then
Desktop>Gnome>Peripherals>Keyboard>Indicator and check the box on the right side that says "showFlags"

logging in and out,

turned out the indicator icon to be useless.

So, I installed from synaptic indicator-applet v.0.4.6 and then with right click on my panel bar I enabled it. 

While doing so I was able to see 3 different options:
i) message icons,
ii) music ones,
iii) language icons

In order to get rid of the first two I went to synaptic and uninstalled:
indicator-messages
indicator-sound
respectively.

For nice flags, I had to download them from:
[http://ubuntuforums.org/showpost.php?p=4459371&postcount=6](http://ubuntuforums.org/showpost.php?p=4459371&postcount=6)

named them:
gr.png
and
us.png
for hellenic and english language respectively,
and everything ok.

And the top panel bar has freed some space.

Regards!

PS: *The solution* mentioned above was enabled for the new applet to word.

PS2: If you are not able to see flags right away, just log out first and log in back.

---

