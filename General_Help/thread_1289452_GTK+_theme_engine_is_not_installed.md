---
title: "GTK+ theme engine is not installed"
date: 2009-10-12
forum: General Help
---

### Post by ashatron on 2009-10-12
Hi,
Im trying to install some nice themes from gnome-look.org but keep getting this message -
"the theme will not look as intended because the GTK+ theme engine is not installed"

ive tried -

sudo apt-get install gtk2-engines
but no luck.

Ive heard of Aurora. is that relevant?

Help appreciated thanks :)

---

### Post by mcduck on 2009-10-12
If the error doesn't actually show any name for the missing GTK engine you can simply ignore the error, it won't affect anything.

In those cases the error is just a result from a common way of setting widgets unthemed to make them inherit the theme from their parent object, this is often done by telling them to use different theme engine but not actually defining the engine to use. Gnome's theme manager get's a bit confused because of this and as a result shows the error you see.

However, if the error actually tells what engine it's missing you of course should install that engine.

So, if you see message like this, you can ignore it:
> the theme will not look as intended because the GTK+ theme engine "" is not installed.


But if you see, for example, something like this, install the engine the message says is missing
> the theme will not look as intended because the GTK+ theme engine "Aurora" is not installed.


---

### Post by ashatron on 2009-10-12
thats very helpful!
thank you sir :)

Now can you recommend any nice themes?? :D

---

### Post by CatKiller on 2009-10-12
> **ashatron said:**
> can you recommend any nice themes?? :D

[These]("http://www.bisigi-project.org/?lang=en") are quite nice (with one or two small flaws).

---

### Post by mcduck on 2009-10-13
> **ashatron said:**
> thats very helpful!
thank you sir :)

Now can you recommend any nice themes?? :D

Depends on what you like. :)

But I really, really love the Gnome-colors/Shiki theme set, it's very professional and not messy, comes in nice set of colors and is one of the few truly complete theme sets (meaning that it includes wallpapers, icons, GTK and GDM themes and lock screen dialogs, and all this in many colors).

[http://code.google.com/p/gnome-colors/]("http://code.google.com/p/gnome-colors/")
They also have a PPA repository for Ubuntu, makes installing & keeping the theme up to date very easy:
[https://launchpad.net/~gnome-colors-packagers/+archive/ppa]("https://launchpad.net/~gnome-colors-packagers/+archive/ppa")

(I must say I really don't like the Bisigi themes linked in the above post, they look nice in the screenshots oj the web page because the wallpapers are pretty, but the actual themes themselves are ugly..)

---

