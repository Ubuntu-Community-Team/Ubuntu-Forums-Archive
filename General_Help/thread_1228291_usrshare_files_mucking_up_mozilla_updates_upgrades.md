---
title: "usr/share files mucking up mozilla updates/ upgrades"
date: 2009-07-31
forum: General Help
---

### Post by rainserpent on 2009-07-31
I recently encountered a problem upgrading Songbird. After uninstalling the previous version *completely* with Synaptic, and reinstalling with gdebi, the program would give me an error box stating that another version was already running. 

I had to delete the usr/share/songbird file after the uninstall to stop this. I vaguely remember having problems with a Firefox update that just about drove me mad until I did this.

If anyone has more insight into this or a way to keep this from happening in the future, I sure would like to hear from you.

-Paul

---

### Post by Zorael on 2009-08-01
Does this happen if you (temporarily) rename your profile directory?

I seem to remember reading that Songbird/Firefox/Thunderbird/general Mozilla apps create a lock file in there, and if they detect it still existing upon start they'll freak out like that. Reasons for it still existing could involve general crashes, but it wouldn't explain why it worked with your earlier version and not with this new one.

---

