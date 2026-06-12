---
title: "Update to Kernel 2.6.32-38"
date: 2012-02-17
forum: General Help
---

### Post by shadow of the locust on 2012-02-17
I am currently using 10.04 (lucid) and until my last update had no problems at all.

A recent update to Kernel 2.6.32-38 has introduced some serious performance issues regarding the internet.

Firefox and Chrome both grind to a standstill and grey out for around 5 seconds at a time before refreshing.

Pidgin also acts strangely with some messages going astray and others taking longer than usual to send and receive.

The only other problem that I noticed was that the volume up/down button at the top sometimes has no slider to change the volume.  Sometimes I can't even select any options from it at all.

Everything works fine if I boot into Kernel 2.6.32-37, so its not like I'm completely stuck, but if anyone has any suggestions as to what went wrong in the last update, it would be much appreciated.

Thanks.

---

### Post by ajgreeny on 2012-02-17
I have no idea about that recent update as I do not use the 2.6.32 kernel any more.  For a long time now I've been running 10.04.3 using the kernel 2.6.35, curently 2.6.35-32, from the standard ubuntu repos with the proposed updates enabled using synaptic package manager, or software-sources.  After kernel installation I again disable those proposed repos to avoid other packages being updated.

I have found that to be problem free, and it will have the advantage to you, that it will be at the top of the grub list, therefore booted by default, rather than the 2.6.32-38 kernel which gives you the problem.

Give it a try;  you can always remove it if you have no better performance, and go back to the current state.  You can then remove the 2.6.32-38 kernel and pin the current -37 kernel version to avoid the continual update notifications.

---

### Post by shadow of the locust on 2012-02-17
Just as a test, I reinstalled flash and this problem seems to have gone.

I'll keep your reply in mind if it breaks again though.

Thank you for your help!

---

