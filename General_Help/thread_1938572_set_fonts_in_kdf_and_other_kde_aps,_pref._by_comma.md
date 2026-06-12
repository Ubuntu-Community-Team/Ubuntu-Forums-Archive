---
title: "set fonts in kdf and other kde aps, pref. by command, how to?"
date: 2012-03-09
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-03-09
How can I adjust the font size in kdf (kDiskFree) gui display? Ideally I'd like commands I can put in a script that would change the font sizes for all kde aps but any way at all would help. I'm using it under Maverick with the default Gnome 2 desktop in my main boot partition and under Oneiric with the Mate gnome 2 fork on my still-being-tweaked boot partition. Any suggestions would be appreciated.

---

### Post by Dreamer Fithp Apprentice on 2012-03-10
I found part of an answer, not the ideal answer but better than nothing, so if nobody comes up with a better one, at least someone finding this thread by searching for a similar topic can use this. I spent a lot of time installing stuff that was SUPPOSED to do what I wanted, at least according to some tech blog post somewhere but none of them did. Sorry I've lost track of all of the names. Systemsettings was one of the ones that didn't help. None of the directions I found worked as stated. Dunno why. But somewhere along the line I picked up Gtk-ChTheme in System Tools menu, probably when I followed a suggestion I saw somewhere to install something like "kde-core-base" - I don't think that is the right name but it is close. It has a fonts button that brings up a gui for setting fonts and when I set them that way, kdf and k3b both respect the changes.

I'd still like to know a way to do this from the command line so I can put it in my font toggling script if anyone knows the syntax. So I won't mark this solved yet.

Edited to add: I should say I've only so far verified this works on the Oneiric/Mate installation. When I boot into the Maverick later I'll test it there and report back.

---

### Post by Dreamer Fithp Apprentice on 2012-03-10
I was too optimistic. Darn thing changed the fonts on the two kde aps as stated but now it won't change them back. And it seems to have altered the way my system responds to the font changing scripts that had worked fine so that now they only affect some of the fonts they used to toggle successfully but now leave at least one unaffected.

---

