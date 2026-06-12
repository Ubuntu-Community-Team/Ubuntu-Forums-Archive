---
title: "Scheduled Task  Help"
date: 2010-05-15
forum: General Help
---

### Post by Quarkrad on 2010-05-15
Newbie - 9.10   I would like to launch an app at a certain time.  I have downloaded Scheduled Tasks that I understand is a front end to CRON.  As a test I thought I would launch firefox at a specific time.  The gui is straight forward - I set the command to firefox and set a time, but nothing happens.  In the Scheduled Tasks window under Command Preview it just says firefox, nothing else.  As I can launch firefox in command terminal with just the command firefox I assume all I need in Scheduled Tasks as the command is the same. I am obviously doing something wrong - do I need some additional instructions?

---

### Post by Quarkrad on 2010-05-15
bump - help

---

### Post by iponeverything on 2010-05-15
for a graphical app like firefox you have to set the display.

```

export DISPLAY=:0.0 ; firefox

```

---

