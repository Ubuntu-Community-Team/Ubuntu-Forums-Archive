---
title: "Adding too many desktop panels broke Gnome!"
date: 2010-01-22
forum: General Help
---

### Post by auh2o on 2010-01-22
Upon adding a 7th desktop panel (don't ask... or well, do if you want to and I'll explain), Gnome froze up on me and I had to reset the computer. Now I can't login to either a regular *or* a failsafe desktop without it freezing on me before even reaching the desktop. So the obvious question is, how do I delete superfluous panels from the terminal? I reckon it can't be that hard if you know how - which I don't.

I'd appreciate any help on this, since in the meantime I will have to choose Windows 7 in the Grub menu, and who wants to do that if you can avoid it??

By the way, how many panels can one reasonably have in Gnome? Already when I had 5, the autohide feature started acting up on the last panel added (which is why I messed around with a few more to try to figure out what the problem was).

---

### Post by auh2o on 2010-01-22
Alright, I'm ready to answer my own question! After carefully going through my whole ~/.gconf folder I found what I was looking for in /apps/panel/toplevels. The configuration for each panel will be in subfolders under that folder, named panel_0, panel_1 and so on. I had folders up to panel_5. I removed folder #3-5 and rebooted, and could then log in without problem! The extra panels were still there but I could manually remove them.

Let this be a lesson to you other beginners out there - don't add too many panels! ;-)

I figured, why expand a panel across the whole screen when I could divide it up in several - one panel in one corner that held the desktop switcher, one in the other corner that held the user login/logout control, one in the middle that held several application launchers, one extended that held open windows and the notification area, and one on the lower right edge that held just the trashcan! Then it would always fold out when I needed it and not take up space on the bottom panel. But it was when I got to the trashcan panel that I ran into trouble. After setting it to auto-hide, it would not reappear when I moved the mouse to it! It got stuck in hidden position. I then created yet another panel that I dragged to the same location to lure the trash can panel out, and so on...

Oh well, now you know!  I guess I shouldn't try to have more than 4 panels. And if anyone ever gets into the same predicament, hopefully this thread can help!

---

### Post by cwgtex on 2010-02-06
> **auh2o said:**
> And if anyone ever gets into the same predicament, hopefully this thread can help!

You have definitely helped me!  I have only been using Ubuntu for a day and I already had this problem.  I was able to hit ctrl-alt-f3 and get a command prompt and delete the extra panels.  Thanks!

---

