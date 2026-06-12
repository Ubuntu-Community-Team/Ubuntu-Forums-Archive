---
title: "Apparent Bug in XCursor Selector"
date: 2010-09-04
forum: General Help
---

### Post by Artemis Fowl on 2010-09-04
Okay, so I was installing a new cursor, and I found that nothing in the XCursor selector seems to work. You can click on basically anything, but it won't do anything. The pixel size appears changeable, but does not seem to take effect. Sorry about this, but is it a bug or am I just a failure?

---

### Post by ArturoGarcia on 2010-10-04
I got the same problem here, nothing work, it open but is you click something it dosen't do anything.

If someone knows anything please, Post.

------- xxx -------

---

### Post by buddyd16 on 2010-10-04
its a bug in compiz either disable desktop effects or search the forum for the solution its been discussed a few times.

---

### Post by ArturoGarcia on 2010-10-05
Sure!,  I´m so wrong!

Off-Course i know about compiz bug! I use this to solved:

```
ln -s /usr/share/icons/[cursor_theme]/ ~/.icons/default 
```or 

```
ln -s ~/.icons/[cursor_theme]/ ~/.icons/default
```Anyway...

I thought he was taking about **Gcursor**!

[LEFT][COLOR=RoyalBlue][[COLOR=Black]About this BUG: [/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491")[/COLOR]
[/LEFT]
[COLOR=RoyalBlue][ https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491]("https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491")[/COLOR]

...cause it says **_"Select Xcursor"_** on the windows tittle! I confuse my self! (:¬\  sorry.

---------- xxx ---------

---

### Post by ootawata on 2010-10-09
If you want to get your cursor theme working now, here's how to get it going.

Extract your cursor theme onto your desktop (right click and select "Extract Here")
Make sure it's completely extracted (if you cannot find a "cursor" directory, there may be more extracting to do)
Move the folder to /usr/share/icons
You'll need root permissions to move this:
```
sudo ~/Desktop/<cursorthemehere> /usr/share/icons
```
Now open System->Appearance->Customize->Pointer and your cursor theme should be there.

Source: [https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491](https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491)

---

