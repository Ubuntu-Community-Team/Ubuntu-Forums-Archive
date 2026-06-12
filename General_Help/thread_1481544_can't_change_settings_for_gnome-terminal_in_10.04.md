---
title: "can't change settings for gnome-terminal in 10.04"
date: 2010-05-12
forum: General Help
---

### Post by chellrose on 2010-05-12
Editing the profile in gnome-terminal has absolutely no effect on the appearance.  I can change background color, transparency, image, etc. in the profile edit window, save changes, and the _actual_ terminal appearance does not change at all.  I did make sure to switch to the edited profile after editing :) -- to no avail.

The default navy-on-light-blue isn't bad, but the light-green default for executables is effectively completely invisible on the light blue background.

Is this a bug?  Or does someone have a workaround?

FWIW, gnome-terminal in 9.10 was completely customizable :)

---

### Post by ectospasm on 2010-06-09
I've noticed the same issue.  The transparency slider has absolutely no effect.  I'll search for bugs on launchpad which might already have this bug listed.  If not, I'll file an issue and link to it here.

---

### Post by ectospasm on 2010-06-09
There's a workaround for the transparency issue, it may fix the other settings as well:

[LIST=1]
[*]Open gnome-terminal
[*]Click Edit/Profile Preferences
[*]Select the Background tab
[*]Set the type to Solid Background
[*]Save and close the settings dialog
[*]Close gnome-terminal
[*]Restart gnome-terminal
[*]Open the Profile Preferences again, and edit the Background tab
[*]Select Transparent background
[/LIST]

The transparency slider now works.  I haven't tested other settings.  YMMV

The launchpad bug I found this on is here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/561370](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/561370)

---

### Post by jryanitpro on 2010-06-15
I thought maybe this would correct the fact that when you select solid background it is still faintly transparent. It drives me crazy because I use a solid black terminal and it is distracting for me to still see the images faintly in the background. Not sure if it is related but I thought I'd ask in case you may have noticed the same thing.

Thanks
joe

---

