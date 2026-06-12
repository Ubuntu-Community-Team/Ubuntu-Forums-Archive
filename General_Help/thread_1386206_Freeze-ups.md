---
title: "Freeze-ups"
date: 2010-01-20
forum: General Help
---

### Post by Niniel on 2010-01-20
Hello,

Under 9.10, my laptop frequently freezes up and has to be hard-reset. At first I thought it was a Firefox issue because it happens most often when I'm on the web, but the computer also crashed on me while doing things in Synaptic, so it must be something else.
I have an HP Pavilion z5000 with an Ati Radeon 9600 Mobility, 1.25 GB of RAM and 120 GB hard drive. 

Is there anything I can check to figure this out? Does anybody have any ideas?

Thanks.

---

### Post by wkulecz on 2010-01-20
I'm seeing this a few times too.  I plan to dual boot back to 8.04 later today to see if its perhaps a hardware issue.

Initially my only suggestion would be to make sure all screensavers are disabled. 

Since its a notebook, what follows in not a really helpful suggestion, but if you can leave it plugged in and turn off all power saving options, if the problem goes away, its a good clue its a power management issue.

--wally.

---

### Post by Niniel on 2010-01-21
Thanks, but how would this be a power-saving or a screensaver problem? It happens in the middle of, say, moving the mouse around, or clicking. I mean, I'm willing to disable all kinds of things if necessary, I just don't see how that would help. Can you please explain?
I did not have this problem prior to installing 9.10 so I am convinced it has something to do with this version of Ubuntu. 
My box is always on ac power because the battery is dead (less than 2 % capacity left).

---

### Post by Niniel on 2010-02-23
It doesn't appear to have anything to do with powersaving and screen savers.
My current theory is that somehow the home directory encryption is to blame. So I re-installed 9.10 without that and formatted the partitions with Ext3 instead of 4. Let's see if that makes any difference.
If not, I will either have to wait for the next version of Ubuntu, I'll use something else.

---

### Post by Niniel on 2010-02-24
Shoot, that wasn't it, either. I guess 9.10 and my laptop just don't get along.

---

### Post by Niniel on 2010-02-25
Let's see if disabling the power saving daemon does the trick.

---

### Post by Niniel on 2010-03-05
No, it did not.
Oh well.

---

