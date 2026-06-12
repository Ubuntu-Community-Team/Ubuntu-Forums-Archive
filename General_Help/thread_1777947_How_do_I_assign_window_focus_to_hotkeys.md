---
title: "How do I assign window focus to hotkeys?"
date: 2011-06-08
forum: General Help
---

### Post by sirrobert on 2011-06-08
[B]Setup
[/B]I'm using Ubuntu 11.04 with Unity.

[B]Background
[/B]I've got a pretty simple shell script that tiles my right-side monitor with terminal windows for coding:

```

$ cat gnome-tiles-right.sh 
### The left column.
gnome-terminal --geometry 105x58+2503+0 &
gnome-terminal --geometry 105x59+2553+810 &

#### The second column.
gnome-terminal --geometry 104x58+3200+0 &
gnome-terminal --geometry 104x59+3200+810 &

#### The second-to-right column.
gnome-terminal --geometry 104x58+3840+0 &
gnome-terminal --geometry 104x59+3840+810 &

#### The far-right column.
gnome-terminal --geometry 103x58+4480+0 &
gnome-terminal --geometry 103x59+4480+810 &

```I have a launcher for it in the toolbar.  I click the launcher and my monitor is tiled with terminal windows, and I code.  Life is good.

To switch between windows, I have to either use the mouse (slow), or alt-tab through them all (slower).

[B]Question
[/B]Is there a way I can assign each window to a hotkey (such as, say, SUPER+F1 through SUPER+F8 )?

[B]Supplemental question
[/B]Is there a better way to tile these windows than through this kind of shell script?  Anyone know of an app for this? 

[B]Notes
[/B]I tried "Terminator" but it doesn't give independent windows for each one, it just segregates the main window into terminals.  For various reasons, I don't want that.

---

