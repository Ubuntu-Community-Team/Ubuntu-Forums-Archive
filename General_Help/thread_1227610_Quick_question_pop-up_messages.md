---
title: "Quick question: pop-up messages"
date: 2009-07-30
forum: General Help
---

### Post by kikazaru on 2009-07-30
I'm trying to modify the system pop-up messages that appear in the top right of the screen (volume adjustments, wireless connect events, etc.) because I find them large and distracting.

Could someone tell me what is the program/daemon responsible?

If there's a convenient tool/method for modifying its behavior that would be marvelous of course.

Thanks!

9.04, 2.6.28-14-generic #47-Ubuntu

---

### Post by komputes on 2009-07-30
The process is /usr/lib/notify-osd/notify-osd. It is part of notify-osd package.

To modify it get the source and look at the source code (you need to be a programmer or make many guesses)

```
sudo apt-get source notify-osd
```

From what I know there are no tools to modify the behavior other than editing the source code. If you are interested in proposing the idea, you can register the concept of theming and modifying the size of the notifications at [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)

This article shows a way to turn it off (not sure if this command is the preferred way of doing this)
[http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/)

---

### Post by kikazaru on 2009-07-30
Excellent, thanks for the information.

I'd rather have them off than as they are, but the little pop-ups I used to get with 8.10 were reasonable (the ones with a little countdown-to-disappear clock). Maybe I can downgrade notify-osd or something. I've got better things to do than rewrite the source, but I guess there might be some basic 18th century surgery I could apply.

Thanks again for the answers.

---

### Post by komputes on 2009-07-30
Martin Pitt wrote up how to revert to the standard GNOME Notifications on his blog:
[http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)

> To enable this feature, apt-get install gnome-stracciatella-session and select the “GNOME (without Ubuntu specific components)” session in gdm.

pitti rocks!

---

### Post by kikazaru on 2009-08-06
Much obliged. Thanks!

By the way, I made a little script to switch the notification system at the user level, as copied below.

I was wondering where I should execute this... in the .login script? I want it to run every time I open a gnome session I guess... is there a script intended for user customization? Also, where is notify-osd first launched? And.... is there a nice way to find out for myself without having to ask?

Thanks again!

#!/bin/bash
`ps auwxx | grep "/usr/lib/notify-osd/notify-osd" | grep -v grep | awk '{printf("kill %s\n", $2)}'`
`ps auwxx | grep "/usr/lib/notification-daemon/notification-daemon" | grep -v grep | awk '{printf("kill %s\n", $2)}'`
( /usr/lib/notification-daemon/notification-daemon & )

---

### Post by johnl on 2009-08-14
Hi, 

If you're interested in changing the colors/transparency, I have written a patch that you can apply to the notify-osd source code that allows you to specify these options.  There's a walkthrough on how to do this [here]("http://reznor.homelinux.net/story/patching-notify-osd-allow-color-selection").

Unfortunately it doesn't let you change position or size, if that's what you are looking to do. 

Hope this helps!

---

### Post by kikazaru on 2009-08-16
Cool! Very nice.

---

