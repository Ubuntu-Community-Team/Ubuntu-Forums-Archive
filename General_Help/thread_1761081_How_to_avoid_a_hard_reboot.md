---
title: "How to avoid a hard reboot???"
date: 2011-05-17
forum: General Help
---

### Post by nhaskins on 2011-05-17
My friend clicked on a Vimeo video in Firefox, and my computer became "partially frozen". The video stopped, but the audio continued to play to the end, but I couldn't clear the video. I pressed ctrl-f2 to switch to my other desktop, but it just brought up a blank screen, and switching back makes no difference.
As it stands I have a black screen with my mouse cursor on it (I can move the cursor, yes). I'm new to linux, and I want to know if there are any keyboard shortcuts I could try to fix this. I'd rather not hard reboot whenever I run into a problem, I just don't know the terms to google for.
Any help is most appreciated.

Neil

---

### Post by TeoBigusGeekus on 2011-05-17
If you can launch a terminal
```
killall -s 9 firefox
```
It might be firefox-bin, can't remember: try'em both.

---

### Post by AlphaLexman on 2011-05-17
You should also look at the 'Raising Elephants" system call. It is actually an acronym for some keystrokes explained here:[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by nhaskins on 2011-05-17
I tried that (killall -s 9 firefox), it said "no process found", but from terminal I ran ```
sudo shutdown -r now
``` (which restarted the computer) and thus avoided "the dreaded hard reboot".
Thanks for your help

---

