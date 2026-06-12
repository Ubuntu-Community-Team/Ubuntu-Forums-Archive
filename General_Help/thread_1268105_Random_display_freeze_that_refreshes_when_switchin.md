---
title: "Random display freeze that refreshes when switching Ctrl+Alt+Fx"
date: 2009-09-16
forum: General Help
---

### Post by reader4 on 2009-09-16
Very strange problem.  In the last month or two I have two 64-bit Ubuntu 9.04 systems - this one with NVIDIA GeForce 1400 and another with Intel 9xx - that will randomly lock up the display.  Everything else is running fine, as I can see when SSHing to the boxes from another machine.  Normally the freeze locks out the keyboard and mouse as well and I have to restart X remotely.  This time, the display froze but did not lock out the mouse/keyboard.  The interesting/weird part is that if I click on an area of the screen, or type, nothing happens unless its the workspace switcher - then I see the workspace change.  However, if I use Ctrl+Alt+F3, say, to switch to a different session then come back to my X-session with Ctrl+Alt+F7, I see the changes that occured from my typing/clicking.  So, by using this procedure, I was able to click the restart button.

Nothing in the syslog.  I'm wondering where to start tracking this down to create a reasonable bug report. I'm not sure whether this would most likely be a hardware problem, graphics driver, OS/GUI trouble, etc.  The fact that I could interact with the GUI but not see the changes in realtime might help...

---

