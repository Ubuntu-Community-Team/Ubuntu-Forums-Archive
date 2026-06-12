---
title: "Guest session eating too much resources"
date: 2009-11-12
forum: General Help
---

### Post by Fibonacci on 2009-11-12
I'm using Karmic on an Intel Core2 CPU @ 2.16GHz. Recently I've noticed that the guest session runs slow, and gnome-system-monitor shows both cores are being used at least at 50% - even when I'm doing nothing. No process, though, is shown as eating that much CPU.
This, however, doesn't happen on my main session, **even when the guest session is open**. Moreover, when I go back to my main session, the CPU usage goes down to under 5%, as shown by both gnome-system-monitor and htop. CPU usage shoots again through the roof when going back to the guest session.

Strangely, I'm using Compiz on my main session and Metacity on the guest one. Isn't Compiz supposed to be more resource-intensive than Metacity? Why is this happening then?

UPDATE: I discovered through htop that it is /usr/bin/X which is eating that much CPU. This does not show up in gnome-system-monitor. But then again, shouldn't Metacity be lighter than Compiz?

---

### Post by P4man on 2009-11-12
I think the issue is your videocard which can not do 2 compiz sessions, so ubuntu reverts to software compositing in the guest session, which taxes your cpu.

Metacity is not lighter than compiz in the sense that if it has to do compositing and can not use  GPU acceleration for that, then it will eat a lot of cpu cycles.

---

