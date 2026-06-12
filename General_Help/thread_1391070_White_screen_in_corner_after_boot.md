---
title: "White screen in corner after boot"
date: 2010-01-26
forum: General Help
---

### Post by sithlordkyle on 2010-01-26
I have been using Netbook Remix 9.10 and it's been great until this morning.

Today when I turned it on, after Grub and the loading screen, the system brought up a smaller white screen in the corner with my username@machinename"~$ as the first line.

This looks like a terminal window.  I can see my folders and use the system but I get no GUI anymore.  Not sure why this is happening.

Tried booting into Recovery and updating the system, but to no avail.  I've also searched the forums for the last few hours but have not found anything similar.

Anyone have any idea what to do?

**UPDATE:** typing gdm in this terminal windows shows:

WARNING: **: Failed to acquire org.gnome.DisplayManager
WARNING: **:Could not acquire name: bailing out

Not sure if this is relevant to my problem or not.  However, I do remember this happening on my desktop version of 9.10... that was solved by installing 9.04.

---

### Post by sithlordkyle on 2010-01-26
Typing gnome-session into this white terminal box causes an infinite loop of message, some errors, but too fast to read as the screen blinks with each reiteration.

---

### Post by sithlordkyle on 2010-01-26
Still nothing working, have resisted reinstalling 9.04 to save all the reconfiguration.  Found more forum entries with the similar problem and no solutions that work.

Am currently trying to add a new user to see if that user experiences the same issue as my original.

**UPDATE: **new user experiences the same problem as original user.  reconfiguring xorg didn't work either.

**UPDATE 2: **startx tells me it's already running

**UPDATE 3: **stopping GDM takes me to a pure black screen with white text and requires me to log in again, starting GDM from here just returns me to the white terminal screen

**UPDATE 4 FINAL: **so GDM is running and apparently so is startx or whatever process that is.  i've tried everything i could find and nothing worked.  so now i shall try Moblin and be rid of the cursed Karmic Koala.  what a waste of time.

---

