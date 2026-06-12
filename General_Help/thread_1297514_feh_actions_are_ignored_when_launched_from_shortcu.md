---
title: "feh actions are ignored when launched from shortcut"
date: 2009-10-21
forum: General Help
---

### Post by Kotofeich on 2009-10-21
Hi,

I'm not sure if this is a feh bug or a launcher bug per se. I could not find any information on this elsewhere so I hope you can help.

I tried out feh's slideshow feature and liked it except that files deleted from feh bypass trash. I decided to try out the --action option as follows:

feh -zsfrZFD3 --action "gvfs-trash %f" /home/ted/sn

this works as expected when run from bash

I then decided to set this to a shortcut/custom launcher in ubuntu 9.04 with Gnome like this: right click on the panel -> add to panel -> custom application launcher -> pasted the command into the command field.

When I launch feh from this shortcut, feh launches properly, but the action does not work.

---

