---
title: "How to exclude windows from trail-focus transparency effect"
date: 2012-05-09
forum: General Help
---

### Post by Marko90 on 2012-05-09
Hi.
I am using a trail-focus plug-in for compiz to make my windows little bit transparent.

I would like to know (if possible at all) how to exclude windows from the list of windows that is being affected by that plug-in. For example; Firefox and Chromium are difficult to use when transparent, and media players like vlc and totem do not  look pleasant while playing video.

This is how the my window list for trail-focus plug-in  looks like:

((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)

Thanks

---

