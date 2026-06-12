---
title: "gimp error while loading shared files"
date: 2012-02-20
forum: General Help
---

### Post by rikilshah on 2012-02-20
A few days ago, I tried installing gimp-2.7 development snapshots. After using it for a while, due to some issues I had to re-install gimp-2.6. So I just uninstalled the previous one tried installing gimp2.6 using synaptic but every time I got error showed in screenshot attached. I tried uninstalling libbabl and libgegl and then did fresh install of gimp2.6 from Ubuntu software center. Still problem is persisting.I am using Ubuntu 11.10.

What should I do now?:confused:

---

### Post by Ms. Daisy on 2012-02-21
If you don't get any better advice, I would remove all things gimp using purge in a terminal. (I'm not sure of the syntax, I think it's sudo apt-get purge gimp but hopefully someone can chime in.)

Then I would install gimp from the software center- that one is version 2.6.11.

---

### Post by ageofsteam on 2012-02-21
> **Ms. Daisy said:**
> If you don't get any better advice, I would remove all things gimp using purge in a terminal. (I'm not sure of the syntax, I think it's sudo apt-get purge gimp but hopefully someone can chime in.)

Then I would install gimp from the software center- that one is version 2.6.11.

Wouldn't that also delete the custom brushes, patterns etc. in the gimp-2.6 folder in his home directory?  I've never tried purging GIMP, but it seems like that would also get rid of all his custom tools (unless he made a copy of those folders.) :?  I'm not sure if it would (or if he even has custom brushes etc.) but it would be bad to lose them...

---

### Post by rikilshah on 2012-02-21
@Ms Daisy : Let's just tried doing similar thing. I uninstalled gimp from Synaptic and then installed from Software center. But as you say, i will try to purge gimp and then again install it.


@ageofsteam: I don't have any data which I want to backup, so I'll just try purging it.



Thank you buddies!

---

