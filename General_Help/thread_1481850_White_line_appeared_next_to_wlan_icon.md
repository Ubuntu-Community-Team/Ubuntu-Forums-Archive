---
title: "White line appeared next to wlan icon"
date: 2010-05-13
forum: General Help
---

### Post by N_L on 2010-05-13
When I turned on the laptop it came like that, never happened before. Here's the screenshot:
[IMG]http://sites.google.com/site/nolimitss/Screenshot.png[/IMG]
Any thoughts?

Edit: Upon upgdating and restarting it's gone. Sorry for post, my bad

---

### Post by N_L on 2010-05-13
Ok I was wrong, it wasn't fixed. Not it appeared next to Desktop icon down left corner and some icon duplicated. Like volume control and after restart chat one.
Also old kernel is showing in grub that I uninstalled.
Also icons are messed up. Like wlan icon shows on when its turned off, can't press some and hovering over them doesn't show anything.

Don't think update did this, worked fine. Just started it this morning and this happened. Try booting recovery but it gets stuck at _ after Done.

---

### Post by N_L on 2010-05-13
Old kernel is showing in grub even tho I uninstalled it. Help? :/

---

### Post by N_L on 2010-05-14
White lines and double stuff ain't happening anymore but old kernel still showing after removal. How do I delete it?

---

### Post by N_L on 2010-05-19
Now my whole wlan icon is white, and 3 dots next to show desktop icon were white but went off.

Hmm this is rather strange, plus old kernel won't leave.
Any thoughts, anyone? :|

---

### Post by N_L on 2010-05-23
I feel special, I'm only one with such problem haha

---

### Post by mc4man on 2010-05-23
Well I actually have the notification area go 'south' probably once a day or so - though here it's usually the wireless icon turns into a 2nd non-functional speaker icon.

While it's just annoying at worst, to 'fix' I just remove the notification area and then add back in
(r.click on the 'bad' icon or slightly to the left - remove from panel and then r.click - add to panel

(the notification area seems to be one of several changes started lucid that aren't really implemented yet, or whatever...

I think lucid may have an inordinate amount of 'corner case' bugs and randomly repeatable inconsistent (mis)behaviors

---

### Post by N_L on 2010-07-24
Haven't been using laptop for a while so today I decided to format HDD and install ubuntu fresh.
So I did and it worked great. Then I installed bunch of applications(amsn, music players, vlc, restricted extras etc) and upon restart the problem is back!
It appeared next to show desktop icon but went away and also this happened:
[IMG]http://sites.google.com/site/nolimitss/ubuntuproblem.png[/IMG]
Can't press the button thats supposed to be behind that(shutdown, restart etc).
It very likely some applicaation I installed is causing this so what would be the best way to go troubleshooting this? Can I find like a list of stuff I installed myself recently or something like that(instead of looking at huge list of all that's installed) and start removing until it goes away?

But I have no idea what could be causing this, I didn't install anything beside normal/casual stuff hmm.

---

### Post by N_L on 2010-08-01
Well I tried a lot of things but no permanent solution, it comes and goes. 
Best thing to do is: killall gnome-panel
which will reset it and then it works fine, so if anyone has same problem that's the easiest way to go about.

---

### Post by junapp on 2010-08-01
for what it is worth:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448)

---

### Post by Dave_gb on 2010-08-01
I get this as well.
What I do is right click the panel, select *properties* and then tick *show hide buttons* and then untick *show hide buttons*. Seems to do the job.

---

