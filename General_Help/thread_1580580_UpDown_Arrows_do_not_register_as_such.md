---
title: "Up/Down Arrows do not register as such"
date: 2010-09-23
forum: General Help
---

### Post by Doctadrez on 2010-09-23
Ubuntu 10.04, 2.6.32-24-generic

For some random reason, my up/down arrows do not work any more. I noticed while trying to cycle through commands in the terminal.

I ran XEV to see if they were working, and yielded this result: [http://pastebin.com/K945JDAq]("http://pastebin.com/K945JDAq")

I checked to make sure my keyboard settings were USA and everything checked out fine. I have no global hotkeys and disabled any others, and have been left scratching my head.

Any input is very much well appreciated.

---

### Post by Doctadrez on 2010-09-24
It managed to fix itself, for some reason. No restarts or anything. They just started working again. Hmmm :/

I was able to reproduce the xev outputs while the buttons worked by simultaneously holding CTRL+ALT and pressing up or down.

---

