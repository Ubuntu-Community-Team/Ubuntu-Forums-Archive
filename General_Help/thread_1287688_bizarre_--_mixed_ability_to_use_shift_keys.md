---
title: "bizarre -- mixed ability to use shift keys"
date: 2009-10-10
forum: General Help
---

### Post by JackD on 2009-10-10
i'm unable to get the shift key to work correctly in gnome. but the caps lock works alright. 

on the other hand, if i pop over to a terminal  ctrl shift f1, etc, then everything works fine.

if i open a terminal inside of gnome, the shift still doesn't work.

so, 1 - it's not a keyboard problem, 2 - it works fine in tty. 

ive checked the selected keyboard -- and its good. im using a t61 thinkpad.

this is a new problem that happened after an upgrade, so i'm sure something changed -- i just cant' figure out where to look

tried restarting and my login password includes an uppercase character that works fine . . . until i'm in gnome.

what is it

----------------------------------------

Follow-up:

I still have the problem. However, it's not any configuration with X, xmodmap, and maybe not Gnome. I've checked gconf and some other stuff--to no avail.

However, when I created a new account, the new account doesn't have the same problem. Now, I have to ferret through all the home configuration files that have something to do with keyboard mapping.

----------------------------------------

Finished:

There wasn't a problem with environment variables, and because a new account did not have the same issue, I renamed the .gconf settings and the shift key returned. I returned the .gconf settings and, automagically, everything is fine (except that I lost many gconf settings ... weird).

---

