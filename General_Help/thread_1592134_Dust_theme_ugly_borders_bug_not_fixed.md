---
title: "Dust theme ugly borders bug not fixed?"
date: 2010-10-10
forum: General Help
---

### Post by Andy06 on 2010-10-10
[https://bugs.launchpad.net/dusttheme/+bug/563218](https://bugs.launchpad.net/dusttheme/+bug/563218)

It says Fix committed and has been that way since June? Yet the bug is still present in 10.10?
Does Fix Committed not mean Fixed yet or Released and that they are still looking to merge the changes into final code?

---

### Post by mc4man on 2010-10-11
> It says Fix committed and has been that way since June? Yet the bug is still present in 10.10?
Does Fix Committed not mean Fixed yet or Released and that they are still looking to merge the changes into final code? 

In this case it means the 'fix' has been applied to the theme but it has not been included in the theme package that the dust themes are in.

You can however use the 'fixed' theme, gave it a try and seemed ok. (I use a slightly modded ambience

There seem to be several ways to add the newer dust, if desired I'll retrieve the link and how I did 
screen shows the 'new' dust in appearances menu

---

### Post by Andy06 on 2010-10-11
Why would they not update the packages?

Can QA or the UIX team not see what a visual atrocity the current ones are?

Instructions would be very helpful (if its just from the Dust PPA, I'll go do that right now)

Thanks

---

### Post by mc4man on 2010-10-12
Don't know about the ppa - give it a try

Got the new themes w/ this (need bzr installed

Made a folder named dust, cd'ed to it and ran 
```
bzr branch lp:dusttheme
```

After retrieving inside you'll find a readme describing various install methods, take your pick

(I used 'make package' and then installed from the dialog in Pref's -  Appearance - Theme - Install

---

### Post by Andy06 on 2010-10-21
So basically that's some development branch then?

Coz the Artwork page and the repos both contain the older one with the ugly borders. The developers aren't replying on launchpad.

---

