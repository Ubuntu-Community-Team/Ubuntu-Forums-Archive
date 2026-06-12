---
title: "Totem fullscreen annoyance."
date: 2006-01-28
forum: General Help
---

### Post by iam10ninjas on 2006-01-28
Whenever I view a video in totem and press F to go fullsecreen, it plays the video on my primary monitor no problem. 

When I move the mouse, the controls appear at the bottom of the screen and don't disappear, so I exit fullscreen.

When I press F again to get back into fullscreen mode, it stretches the video across both my monitors, rendering it unwatchable.

Does anyone know of a setting or an xorg.conf option that I need to prevent this from happening. I have an NVidia graphics card with twinview enabled.

---

### Post by ktulu1115 on 2007-05-08
I've got the same or a similar issue for the past few releases (Dapper, Edgy, & now Feisty).  Have no idea why it happens, seems to be related to the multi-display functionality.  I have an Nvidia card as well, but am not using Twinview.

On my system if I fullscreen a video in Totem and keep the cursor stationary the controls will not appear.  If I move it, they appear and do not disappear if the cursor is left stationary again or is moved to another screen.

A hack-ish workaround I found involves loading a file in Totem, then QUICKLY hit 'F' to fullscreen while simultaneously moving the mouse cursor to the other display.  On my system, Totem takes a second (probably more like 250ms in reality) to go to fullscreen mode and if you move the cursor off before it switches the playback controls won't appear.

Of course, it's a lot easier if Totem isn't cached in memory and it also helps to have the cursor practically on the screen boundary already.  Also, you have to keep the cursor off that primary screen (with the fullscreened video) or else the controls will re-appear and be stuck there again.

---

### Post by K-Rich on 2008-03-23
I had the same issue about 5 minutes ago... i did however find the answer

in the file ~/.gnome2/Totem state.ini the top 2 lines had the window to the full resolution, i solver the issue thus:

rm ~/.gnome2/Totem/state.ini

and restart Totem...

Hope this helps

K-Rich

---

