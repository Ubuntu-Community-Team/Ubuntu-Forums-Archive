---
title: "Rhythmbox - SLOW startup"
date: 2010-06-15
forum: General Help
---

### Post by gunksta on 2010-06-15
I looked through the forums and I don't see too many references to this so this may be a somewhat uncommon situation. I am running Lucid and it was a clean installation.

For some reason, Rhythmbox takes several seconds to start on a 2-core laptop with 4G of RAM. Since it's a work laptop, the music collection is trivial (10-15 albums). All of the music is local. Banshee starts up much faster, in spite of the fact it's a Mono based app. 

In Rhythmbox - I tried turning off the new Ubuntu1 music store and most of the other plugins but I don't see an improvement in the startup time. When I start rhythmbox from the command line, I don't see any errors or warnings.

Thoughts?

---

### Post by LoneWolfJack on 2010-06-15
takes like 3 seconds to load on a dual Xeon 3,8 GHz on intrepid. maybe give audacious a try? its in the repos.

---

### Post by gunksta on 2010-06-15
I thought I should try deleting my config folder, on the off chance that something in there is screwy. But, that's easier said than done. I don't see a rhythmbox folder in either .gnome2 or .config. I suppose rhythmbox may just use gconf, and I'm not wiping that out for one errant program.

I may try installing that Guayadeque thing.

---

### Post by Krzysztow on 2010-09-03
Try to deselect "Watch my library for new files" in Edit->Preferences [Music Tab]. It seems to work for me. Of course You pay the price of being forced to add new files manually - I can deal with it, it doesn't change so much and if so then I just drag and drop.
Hope it helps.

---

### Post by gunksta on 2010-09-03
I did try that, but it still seems a little flaky to me. In the end, I now tend to use other music players. As Ubuntu continues to tweak the default Gnome interface in ways that I'm not sure I need, I have started using a default XFCE interface instead. I like Banshee, but the Mono dependency thing worries me so I have gravitated to Exaile.

---

