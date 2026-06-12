---
title: "Icons gone from taskbar"
date: 2010-07-07
forum: General Help
---

### Post by malel on 2010-07-07
I am running Ubuntu 10.04 and at first there was the icon for Open office quickstart and the icon for network connection . After some updates those two disappeared but I was able to switch off the computer. I have managed to get those two icons back using 'notification area' but the computer will not shutdown now. Has anyone else had this happen and if so how did you fix or do we have to wait for another dubious update?

---

### Post by lidex on 2010-07-07
That thread title is not very descriptive of your actual problem. Exactly what happens when you click on shutdown icon? Have you checked your logs?

---

### Post by malel on 2010-07-07
I had to use the command line to shutdown and when I restarted all was okay.
Is this 10.04 still flakey? because I am not sure if this will be the same next time I shutdown and start up.
I would check my logs if I knew which one to look into and what to look for . So I think that there has been enough said about icons disappearing from the taskbar and would consider this one resolved.

---

### Post by Absorbed on 2010-07-20
I think I'm having a similar problem.

All the stuff on the taskbar on the top of my screen is fine most of the time, but sometimes when I log in the shutdown button disappears, and sometimes the social networking thingy disappears as well. The clock tends to be fine, but the other two things disappear because you also get a copy of the clock printed to the right of the clock, if that makes sense, overwriting the shutdown button. Sometimes its a copy of the social networking thing which is printed over the shutdown button.

I've been working around this by adding a log out user button to the top menu, and then just logging out and then in again, and then it seems to fix itself.

I'll try and get a screenshot of it, since my description is pants.

---

### Post by lidex on 2010-07-20
I would try using a different theme.

---

### Post by Absorbed on 2010-07-28
I moved the clock and the notification area, and now it appears to be fixed and I cannot recreate the problem.

---

### Post by Absorbed on 2010-08-19
The problem reoccurred and I got a screenshot this time.

Edit: Oh, and rebooting tends to fix the problem.

---

### Post by ashen on 2010-09-24
I have also had this problem - no idea why it happens but you can get the button back by typing

```

sudo killall gnome-panel

```

This will restart the gnome panel applet and bring back all your buttons and widgets.

It is really annoying though - I've been using Ubuntu since 6.04 and this release is the flakiest I've tried.  I would go back to 9.04 (which was rock solid) but it's too much effort ...

Alex

---

