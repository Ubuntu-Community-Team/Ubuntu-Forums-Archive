---
title: "I was about to praise Xubuntu 9.10"
date: 2009-11-10
forum: General Help
---

### Post by slumbergod on 2009-11-10
After finally sorting out my annoying 9.10 issues I was going to post a nice comment saying how well Xubuntu Karmic is finally running. Then I ran into another annoying bug. I tried to see if the bug was already reported but I went round and round in circles without even working out how to do it.

Anyone else experienced this in Xubuntu?

In Brasero or Gnomebaker (or just about any app) knock the F1 button to bring up help. Up pops the Gnome-Help window...then nothing. The CPU spikes until it reaches 100% and I have to shut my pc down with the power button because the entire desktop has hung.

The only solution to this (I accidentally knock F1 when I am typing numbers) was to delete the gnome-help file. At least I just get a warning that the file doesn't exist now instead of having to restart.

Ideas anyone? If no one else experiences this in Xubuntu then it isn't a bug and I won't try and work out how to file it.

---

### Post by JustinR on 2009-11-10
I haven't noticed this in Brasero but trying to replicate that doesn't work - but the help files do take up a lot of cpu (50%) or so.

---

### Post by slumbergod on 2009-11-10
any idea how to do a reinstall of just the files relating to gnome-help? I can't find a package by that name so it must be part of something bigger. I just can't work out which one.

---

### Post by JustinR on 2009-11-10
Unfortunately, I don't, I'm not sure if you can reinstall help files but maybe someone more experienced can help!

---

### Post by slumbergod on 2009-11-10
I think the problem is just with the help engine rather than actual application help files for each application. I never actually use help but I do knock F1 when I am typing sometimes which is why it'd be nice to fix it.

---

### Post by winotree on 2009-11-10
This is what I've got for the help files -- I remember adding them because they don't come with Xubuntu. 

yelp
gnome-doc
gnome-doc-utils *

* not sure if I added this or if it was downloaded with gnome-doc

Hope this works for you.

---

### Post by slumbergod on 2009-11-10
Thanks for the suggestion. I reinstalled them but couldn't find gnome-doc in synaptic so tried ubuntu-doc instead. Unfortunately, it didn't fix it...same hang once the help window pops up. 

I'll just manually remove the gnome-help executable again so it doesn't lead to another lock up when I knock F1 by mistake.

Looking in synaptic, it appears that yelp is the package responsible for creating the gnome-help file. So now I will see if anyone has reported issues with yelp.

---

