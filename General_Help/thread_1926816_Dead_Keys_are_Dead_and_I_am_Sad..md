---
title: "Dead Keys are Dead and I am Sad."
date: 2012-02-16
forum: General Help
---

### Post by polt on 2012-02-16
Hullo!  I am trying to use a Brazilian Portuguese keyboard layout, but the dead keys are not working.  If I type dead key + letter, it merely types the letter, Like this- eao
Yup, I just typed those with dead keys!  Anyways, I also tried the US International layout with dead keys, and those keys also didnt work.

I looked at several threads where similar problems came up.  Some users fixed the problem by removing references to scim in the ~/.xinput.d directory.  Another user removed some things from the .profiles file in home.  Neither of those cases applied to my situation so I am now at a loss for what to do.  Anyone have some ideas?  

Thanks!!
:guitar:

---

### Post by polt on 2012-02-18
Could this have anything to do with the fact that there is no Brazilian keyboard entry added to the .xinput.d folder?  All I have in there is en_US
---------------------------
Update:  Actually, it looks like the AltGr key works when in the US International keyboard layout.  But any time I try to do a key combination where I type an accent followed by the letter, it just types the accent then the letter, or it types only the letter.  This goes for the special keyboard layouts, as well as for the compose key.
---------------------------
Update 2, 19 Feb: Well, I still haven't figured this out, but I did learn how to edit the Brazil keyboard layout so that I can now use the Alt key to type the characters I want, and forget about the dead keys.  If anyone is interested in doing that kind of thing, the files are in ```
/usr/share/X11/xkb/symbols
``` and are really easy to edit.  You need only restart X for the new changes to go into effect.  This website has some helpful pictures: [http://hack.org/mc/writings/xkb.html]("http://hack.org/mc/writings/xkb.html")

---

