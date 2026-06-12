---
title: "Evolution Calendar View icons broken"
date: 2009-12-17
forum: General Help
---

### Post by Ubunthree on 2009-12-17
I was playing with Evolution Calendar's "View / Current View / Define Views..." settings just now, and created a "test" view to see what I could do with it. I decided I didn't need it, so I highlighted it in the "Define Views for Calendar" window and clicked "Delete." Problem was, my finger bobbled on the mouse button, and I unintentionally deleted the default "Month View" and "List View" as well. Now, the toolbar icons that switch to those views are still there, but not working. The Day, Work Week and Week icons still work. I tried redefining the two lost view-options but was unable to. I tried reinstalling Evolution through Synaptic, but that did nothing. I can still get the Month and List views by going through the View menu, but really would like to have those toolbar icons functioning again. Is there a way to revive them?

Thanks!

---

### Post by american.white.pelican on 2009-12-17
Actually, the exact same problem has just happened to me. Funny enough, I also tried reinstalling the Evolution package, to no avail. Not sure how to fix this.

---

### Post by dcstar on 2009-12-17
> **american.white.pelican said:**
> Actually, the exact same problem has just happened to me. Funny enough, I also tried reinstalling the Evolution package, to no avail. Not sure how to fix this.

You can create a new Linux account and then start Evolution to create a fresh profile that you may be able to copy specific bits into your own profile (in the .evolution folder).

The ability to delete default views seems to be a bug that only appears if you have a custom view that actually can be deleted.

I have reported it, so you can both subscribe to it:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/498040](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/498040)

---

### Post by Ubunthree on 2009-12-17
Thanks much for the Launchpad report. I have posted the Steps To Reproduce there.

For now I have just defined new custom views to reproduce the missing defaults, and bring them up via the View menu. Much less convenient, but creating new accounts and whatnot is just a bit more effort than I'm motivated to go to for this.

---

### Post by american.white.pelican on 2009-12-18
Thanks for the idea of how to try to fix this. I'm busy today graduating college and will be away for the next few days, but I'll play around with that when I get back again and see if I can make any progress. I'll post here if I figure it out!

---

### Post by american.white.pelican on 2009-12-22
All right. I spent some time and figured out it wasn't really that difficult after all to restore the default views in Evolution. I simply deleted the .evolution folder in my home folder and when I restarted Evolution the program rebuilt the folder all by itself. I didn't even have to fill out my email accounts and information again. I tried checking it with some locally stored calendar appointments, and even after I deleted the folder all my local information remained as far as I could see. So I'm not sure where that stuff is actually stored, but it was a breeze for me to just delete the folder and let Evolution take care of rebuilding it. I would recommend backing up your .evolution folder first, just in case something goes amiss, but I didn't have any problems with it.

Hope this helps!

---

### Post by Ubunthree on 2009-12-23
Hmmm. Actually that does seem to have worked for me too. Thanks for taking the leap. I guess it's still a bug, but the workaround apparently is easy enough that I won't bother tracking it any more. Now of course I'm curious about where all of that calendar information etc. IS stored, if not in the .evolution folder.

---

