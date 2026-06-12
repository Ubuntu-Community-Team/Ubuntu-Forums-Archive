---
title: "Um... Srange Issue..."
date: 2011-07-28
forum: General Help
---

### Post by mrinsult2000 on 2011-07-28
Basically, If I move my mouse to the bottom right corner of my screen, my computer freezes for a few seconds.  Not just the mouse, everything.  I have Conky running with a 1 second refresh rate, and it hangs as well.

I have done nothing to my computer today besides browse the web.  

I'm running Ubuntu 11.04 x64.  Anyone heard of anything like this?  It only happens if I move my mouse to the bottom right corner, everything else is fine.

I have rebooted already. It happens in Unity, and normal Ubuntu desktop with no effects.

Strangest thing...

EDIT: Thanks to Conky running and showing me high usage processes, I can see that when I move my mouse to the right bottom corner of the screen, Xorg eats up 25% of my CPU (1 core - Quad Core processor).  Once I am able to move my mouse away from that side of the screen, CPU utilization goes back to normal.

Thanks!

---

### Post by 4Orbs on 2011-07-28
You might want to check out [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=1787110").

---

### Post by mrinsult2000 on 2011-07-28
Thanks for the link.  I remembered after you sent me that, that I had experimented with a new video driver recently.  I removed it, went back and used the one from Additional Drivers, rebooted, it works fine now.

Thanks!

---

