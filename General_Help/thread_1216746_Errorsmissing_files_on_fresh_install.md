---
title: "Errors/missing files on fresh install"
date: 2009-07-18
forum: General Help
---

### Post by HyperHacker on 2009-07-18
I just installed Xubuntu 9.04 and am already seeing some missing images:
[img]http://img204.imageshack.us/img204/6956/missingicons.png[/img]

Also, I get some errors on shutdown. First there's a popup message whose meaning I can't decipher:> **Unable to perform shutdown**
org.freedesktop.hal.power-management.shutdown-multiple-
sessions auth_admin <-- (action,result)I have to click Quit, which returns me to the login screen, and shut down there.

Then just before it powers off, another message appears:> Will now halt
Halt: Unable to iterate IDE devices: no such file or directory

None of these occurred on 8.10. I formatted the disk and set up an encrypted LVM (might explain the IDE error?), so nothing from the previous install remains.

---

### Post by HyperHacker on 2009-07-19
OK... now in both Geany and xfce4-terminal I'm seeing text not redraw properly. In Geany when I scroll or switch files, sometimes some of the text is just missing or in the wrong place and stays that way until I scroll it right off the screen or sometimes until I edit something. In the terminal often newly-printed lines don't appear until I scroll up and down a bit, leaving me to wonder why a command has hung when it's actually finished and the prompt just isn't rendering.

Something seriously broken here? None of this was happening before.

---

