---
title: "No desktop when logging in with Unity (Classic works fine)"
date: 2011-08-10
forum: General Help
---

### Post by kaldor on 2011-08-10
This issue used to just happen randomly, but it's been happening on every login for the last while now. I have not changed any settings to cause it.

My PC is set to automatically log in. Unity is the default session. Every time it finishes booting and plays the startup sound, I see only my cursor and wallpaper, and sometimes just a black screen. The fix is extremely easy; I switch to a TTY and back to the desktop, and everything promptly shows up. If I make GNOME classic with no effects the default session, this problem does not occur.

It's also not only during boot; I just reloaded the X server (ctrl alt backspace) and logged in at the GDM screen. Again, just my wallpaper and cursor; clicking does nothing, and nothing showed up until I switched to the TTY and back.

Could it be graphics-related? Using an AMD Radeon HD 6450 with the Catalyst driver found in Jockey. Sadly, I am dependent on the proprietary driver for things that I cannot do with the OSS Radeon driver, so avoiding catalyst isn't an option for me.

---

