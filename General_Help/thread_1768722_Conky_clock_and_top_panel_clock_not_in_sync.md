---
title: "Conky clock and top panel clock not in sync"
date: 2011-05-27
forum: General Help
---

### Post by AntoineT on 2011-05-27
Hello,

I'm using a very simple conky script to diplay the date and time on my desktop. I've noticed that he conky clock is a few seconds early compared to the time displayed in the right hand side of the top panel (Natty). I guess both displays are based on the same "internal" time, so I'm left wondering how this could happen, and how to sync back the clocks.

Antoine

Edit: It seems that Conky is in sync with the system date, while the panel clock is 2 seconds late (on my system). Checked with 
while true; do date; sleep 0.1; done

---

### Post by Habitual on 2011-05-27
what's the value of "update_interval" in your conky rc file?

---

### Post by AntoineT on 2011-05-27
The update interval in conky is one second. But anyway, a larger value would result in  the conky clock being late compared to the panel clock, and not early.

As I mentioned in the edit of my OP, conky is in sync with the system time, and it's the panel clock that's late by a couple of seconds.

---

