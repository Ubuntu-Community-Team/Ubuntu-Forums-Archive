---
title: "Can No Longer Play Ogg files???"
date: 2009-09-20
forum: General Help
---

### Post by WalkerInTheWoods on 2009-09-20
Ok, I don't have a clue what happened here. Today I can no longer play ogg files, .ogg, .ogv, etc. When I click on a file it tries to open in totem but then says that there is no plugin to play these files.

---

### Post by WalkerInTheWoods on 2009-09-21
The problem seems to be totem as rhythmbox plays ogg files just fine.

Edit: Let me be more specific. The problem is with totem xine. I just tried playing both ogg and ogv with totem gstreamer and they worked fine.

---

### Post by Katalog on 2009-09-21
Have you tried installing any of the xine plugins from synaptic (i.e. libxine1-misc-plugins, etc.)? Although I would expect it play ogg files out of the box, unless you compiled it yourself.

---

### Post by WalkerInTheWoods on 2009-09-21
> **Katalog said:**
> Have you tried installing any of the xine plugins from synaptic (i.e. libxine1-misc-plugins, etc.)? Although I would expect it play ogg files out of the box, unless you compiled it yourself.

I just now install a few plugins that were not already installed, but most of them were. Still it won't play them.

It is not that I could never play them. It was playing them just the other day. Then suddenly it stopped playing them. I don't think I have done anything to xine or totem in the past few days. Plus it will play other formats like mp3, wmv, avi, etc.

---

### Post by Katalog on 2009-09-21
I have to admit to being a little stumped here, because theoretically I'm pretty sure gstreamer and xine can coexist. But perhaps when you installed the xine player there was some dependency held back (I've always had either one or the other installed - never both) because it would have created a conflict with something in gstreamer. Just grasping at straws there, really, as I've never used both at the same time.
I suppose you could do the old tried and true method of opening a file with totem-xine via command line and hopefully it will tell you what it's missing (look for lines like "could not find" before the final error"). But change directories to wherever it is that you keep you videos by typing (for example):

```
cd ~/Videos
```and then 

```
totem-xine foo.ogv (or .ogg)
```Of course you would replace "foo" with the actualy name of the video/audio file. So try to open one via command line and see what the output says, that should tell you a lot more than what's in the error message of the GUI application, unless you're willing to spend time combing through system logs for errors to try and pin it down. Let us know what the terminal output is. You never know, it may tell you exactly which library or plugin is missing.

Anyhow, one final, obligatory question. If they play fine on gstreamer, why would you care whether or not they play in xine? Not trying to be a smart alec, I'm just genuinely curious why you would need two different applications to play the same file format?

---

