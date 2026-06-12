---
title: "Conky quirk"
date: 2009-12-08
forum: General Help
---

### Post by CerialPhreak on 2009-12-08
So I thought I had all of the little 'quirks' settled with conky (stalling startup time, etc) until today. I noticed that when you right-click on an item on the desktop conky disappears. It's still running, just not visible. Anyone have an idea how to prevent this?

---

### Post by VCoolio on 2009-12-08
try changing own_window_type to normal (override, desktop and dock are the other options, desktop probably the one causing the issue).

---

### Post by CerialPhreak on 2009-12-08
Got it. Change window type to normal, then set own_window_hints to undecorated,below,sticky,skip_taskbar,skip_pager.

Shouldnt have stopped searching so soon.

---

