---
title: "Japanese input, how to?"
date: 2009-12-17
forum: General Help
---

### Post by LK_gandalf_ on 2009-12-17
Hi all, I have a pc with Kubuntu 9.10, and a friend of mine needs to install a system that let her insert the japanese characters. She usually uses windows until some days ago when I've convinced her to try linux:KS

I've only found old and incomplete guides, and not a complete one to follow.
It seems that Ibus is the best solution, and scim/skim is going to die.
Please, can you provide me a guide to do this? (It could be also useful to have an update guide on the wiki, it's full of students which can benefit of it)
Thank you ;)

---

### Post by Darael on 2009-12-17
SCIM is being replaced by IBus, but so far as I can tell, SCIM is still installed by default in Kubuntu even though GNOME users have had the replacement done. In fact, it is apparently a bit of a pain to get it working properly in KDE - but there's a guide at [http://ubuntuforums.org/showthread.php?t=1322888](http://ubuntuforums.org/showthread.php?t=1322888) - be warned though that it requires compiling IBus from source, which shouldn't be a problem with the guide, but might be a little intimidating. Otherwise, you can use SCIM until Canonical get it sorted, which will probably be for Lucid in April.

Either way, the input method you want to use for Japanese (that's with either IBus or SCIM) is Anthy.
EDIT: IGNORE that! For some users, it seems that IBus does work straight out of the repos in Kubuntu Karmic, so I suggest trying "sudo aptitude install ibus" before the above to get it in place.

---

### Post by LK_gandalf_ on 2009-12-17
Yes, I've tried that guide but without compiling ibus, just installing it from repos. I'll try again following the instructions.

In order to clean the packages which can interfere with ibus (they come from my previous attempts to try scim/skim), should I uninstall all the packages related to "scim" and "skim"?

---

### Post by Darael on 2009-12-17
You can do, but if they aren't listed as conflicts in ibus's dependencies they shouldn't cause any problems beyond being a waste of space. It's still just possible that they might, but I doubt it - I've had (for obscure and complex reasons) both IBus and SCIM running at the same time on a machine without any issues.

---

