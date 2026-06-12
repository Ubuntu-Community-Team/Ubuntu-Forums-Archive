---
title: "gnome-screenshot tip"
date: 2011-08-24
forum: General Help
---

### Post by fbicknel on 2011-08-24
I've used gnome-screenshot for some time.  I like the area select feature, so I can just take a shot of what's interesting on the screen.  Also useful: the ability to just put the screenshot in the paste buffer and drop that in an e-mail instead of creating a file (then attaching it, etc.)   But you have the choice.

For a long time, I've had my PrtScn key (Print in keyboard shortcuts) set to: ```
gnome-screenshot -a
```  But once in a while it would resort to a full-screen shot instead.  When this finally got annoying, I decided to try instead: ```
gnome-screenshot --area 
```This seems to have solved the problem.

For extra flexibility, I have a launcher set up at the top of my screen with: ```
gnome-screenshot --area --interactive
```This brings up a menu starting with the usual area-based screenshot, but lets you select which other mode you'd like instead.

---

