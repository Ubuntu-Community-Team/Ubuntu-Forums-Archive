---
title: "Why can't I update?"
date: 2011-11-04
forum: General Help
---

### Post by liquidmonkey on 2011-11-04
i've done the latest update in 11.10 BUT there is a bunch of updates still available.
they are for (other updates 'ROS') and although there is a check mark in the box, i am unable to click on update as it is grayed out.

what could the problem b here?

in settings, ubuntu software, i have all boxes ticked EXCEPT 'source code'.
the 'other software' tab has 'canonical partners', 'can par (source code), 'independent' and 'ind (source code)' boxes all ticked.

and so is the box 'disabled on upgrade to oneiric ([http://ros](http://ros))'
what does that mean exactly? are any upgrades to ros disabled now IF that box is checked?


thanks!

---

### Post by flipper T on 2011-11-04
updates are generally greyed out if they are being held back. this is normally done if all dependencies have not yet been resolved.

wait 24 hours, update again, and those greyed out updates will normally be available.

you can force these updates through, but this is risky & there really is no point.

my advice, wait.

---

### Post by liquidmonkey on 2011-11-04
its been like that for a week now.
i'm not into forcing it but was more wondering why its like that. thanks!

i even tried checking, unchecking the numerous boxes in the settings for update manager but no love.

when i UNchecked the box for 'disabled on upgrade to oneiric blah blah ros blah blah' the updates disappeared.

fingers crossed to everything working...

---

### Post by WorMzy on 2011-11-04
> **liquidmonkey said:**
> and so is the box 'disabled on upgrade to oneiric ([http://ros](http://ros))'

I'm not sure what that is supposed to be, but (unless you've been playing around with your hosts file) it's not a valid software source. 

Have you been playing around with your hosts file?

What does your sources.list look like?

Got anything in /etc/apt/sources.list.d?

---

### Post by liquidmonkey on 2011-11-04
i don't know what any of that stuff is, so i guess i haven't played around with it :)

---

### Post by flipper T on 2011-11-04
again, the reason that some updates are ¨disabled on upgrade to oneiric blah blah ros blah blah¨ is that dependencies have not been resolved.

my advice, feel free to ignore, is wait.

---

### Post by Old_Grey_Wolf on 2011-11-04
Post the output of this command ```
sudo apt-get update
``` Maybe we can determine what the problem is from that output.

---

### Post by liquidmonkey on 2011-11-04
its all good people.
i'll just wait.
thanks for the help, much appreciated!

---

