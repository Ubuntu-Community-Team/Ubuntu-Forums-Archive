---
title: "Missing icons in Firefox"
date: 2009-12-06
forum: General Help
---

### Post by freesitebuilder on 2009-12-06
Just upgraded to 9.10, and some of my Firefox icons in the navigation bar are missing. A couple are Firefox icons such as history and bookmarks - these appear in the customise dialogue, and I can add them manually, but when I restart they vanish.

Others are from extensions, which usually add automatically and can also be added manually using customise - they don't appear in customise box at all.

I've selected "show icons in menus" in Appearances in case that might be affecting them, but it has no affect.

All my icons appear OK in menus, and on Firefox live bookmarks toolbar.

Anyone else had this, or can suggest a soluntion?
TIA

---

### Post by ajgreeny on 2009-12-06
I think this is a problem of your profile which probably in 9.04 was for FF v3, and now in 9.10 is FF v3.5.  I had the same problem, but luckily I had an install of 9.04 on another partition (for testing things out), so I installed FF v3.5 to that, which when I first ran it, made itself a profile for v3.5 automatically.  I then copied that profile across to 9.10, instead of the profile from FF v3.  Problem solved for me.

If you can't do that just rename the folder in home called ~/.mozilla as ~/.mozillabak, restart FF and see if it is OK.  You will need to make sure you have the bookmarks backup files in your v3 profile first to restore to v3.5, but I don't know about any saved passwords etc etc, though they will be stored somewhere in the old folder, so search and see if you can find them.

---

### Post by freesitebuilder on 2009-12-07
What a dimwit I am! I disabled all my extensions, re-enabled them one by one, and the culprit of course (as I should have realised immedialtely) was that stupid Ubuntu Firefox Modifications. I don't know what it is supposed to do, but it caused havoc on 9.04/Fx3, and it apparently does the same in 9.10 and Fx3.5!

Thanks for your help - it's always the obvious that I miss. :)

---

