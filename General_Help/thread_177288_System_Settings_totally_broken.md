---
title: "System Settings totally broken?"
date: 2006-05-16
forum: General Help
---

### Post by BerkeleyDude on 2006-05-16
I just started using Kubuntu a few days ago. But I already ran into so many bugs in the System Settings program, that I'm really confused - is it really that broken, or is something terribly wrong with my system?

So I wonder what other people have to say... And also, where can I report these bugs?

Bugs:
1) I changed the mouse behavior to "double-click" instead of "single-click". The System Settings still opens items with a single click.
2) If I double-click, it opens the module twice, and breaks completely - the module is overlayed on top of the icons, no "Apply" or "Reset", no way to close it.
3) If I open "Network Settings" or "Login Manager" or "Printers", switch to "Administrator Mode", then go back ("Show All") - then I cannot open that module again. I am told that "the configuration section is already opened". That's great - but how do I access it?
4) My screen resolution is 1024x768. Lots of modules, such as "Network Settings" don't fit in the screen... and cannot be resized to fit!
5) "Network Settings" module:
 a) It's not clear what exactly "Enable Interface" does... If it fails, it disables the interface, and shows no error messages or feedback whatsoever.
 b) If I set the ESSID for my wireless card, click "Apply", and try to enable the interface... why doesn't it actually change the ESSID? I'm back to "iwconfig"... (And that kinda explains why it fails to enable the interface)
 c) How can I setup multiple wireless profiles? Meaning, some open access points, some encrypted ones (and have the key stored), etc. I couldn't figure out how to use the "Network Profiles" tab. It doesn't seem to do anything.
 d) Why is there another module, "Wireless Network", inside "Connections", that has lots of the same options? That's so redundant! Ok, it comes by default with KDE - but if Kubuntu makes its own System Settings program, with its own wireless configuration module... Then why keep the KDE's default one?
 e) Is there any way to have it connect to a "preferred" wireless network automatically? I'm seriously thinking of writing my own daemon now... :(

---

### Post by GeneralZod on 2006-05-16
> System Settings totally broken?

Pretty much :) I always just used kcontrol.

---

