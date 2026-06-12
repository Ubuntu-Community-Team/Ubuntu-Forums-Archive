---
title: "gPodder help"
date: 2011-01-26
forum: General Help
---

### Post by dondiego2 on 2011-01-26
I have been using gPodder with my iPod for a year with no issues and this week it went berserk on me.  The devices tab disappeared and it did not recognize my iPod.  It must have been an Ubuntu update that messed something up because I didn't do anything else.

I have it now so that the devices tab is present but when I try to sync it tells me my device has not been configured and to use the Preference dialogue box to configure it.  So I went into preferences and clicked on the Devices tab and I get another box that says Config UI Missing, use "Edit Config" below.

When I do this I get a list of preferences and as far as I can tell they are set up correctly.

Any help would be appreciated.  I did uninstall gPodder and then installed it again but it made no difference.

I also just shut down gpodder, deleted the .config/gpodder directory, and then re-started gpodder and got a fresh installation.  I went to preferences and clicked on the devices tab and the same thing.  Config UI Missing.

---

### Post by dondiego2 on 2011-01-27
Anybody else using gPodder that has run into this issue?

---

### Post by dondiego2 on 2011-01-27
OK, I figured it out and I'm back in business but I still don't understand what caused the hiccup in the first place.  It's still confusing that gPodder has a "Devices" tab but gives you an error message when you select it.

I found out that in the advanced configuration file I had everything correct except the "device type".  It looks for a specific name of which it does not tell you anything about what that name should be.  I had "iPod" for that selection and apparently I was supposed to have "ipod" instead.  It seems there should be some kind of documentation showing what the accepted device names are.

I'm glad it is working again but bummed about having to reload all my podcast feeds again and pissed that the program would reset like that.

---

