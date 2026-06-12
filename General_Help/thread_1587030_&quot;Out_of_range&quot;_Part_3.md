---
title: "&quot;Out of range&quot; Part 3"
date: 2010-10-02
forum: General Help
---

### Post by ozzynotwood on 2010-10-02
Hi All

I'm still having problems with the "out of range error", but I've made some progress, but still having troubles.

To install ubuntu 10.04, I boot up of the live CD, get to the boot menu and press F1 to display the help screen and a command prompt. I type "live nomodeset" and ubuntu loads off the CD without any 'out of range' errors. When ubuntu loads, I double click "Install Ubuntu 10.04 LTS" on the desktop, and ubuntu does a full install. When I reboot (CD ejected), ubuntu boots of the HD but I go back to having "Out of Range" come up on the monitor, and I cant go any further.

How do I fix this?

I've read hundreds of posts with replies thats start with "open the terminal", to which the poster writes "how? my screen is totally blank!".

This is what I have, a blank screen, with the monitor displaying "Out of Range". Could somebody please provide me with a step-by-step guide to how to fix this. I'm a complete noob, and I do intend to learn how to use ubuntu, but I need to be able to see it first.

Thanks!

---

### Post by decoherence on 2010-10-02
You should be able to add nomodeset to the boot line when grub comes up. Recent versions of Ubuntu don't show grub by default. Hold down the shift key while booting to get it back. Some people report that this doesn't work but I think the timing is just picky, so you might have to try it a few times to get it right.

Then type 'e' to edit the default boot line and add nomodeset to the end. Then type 'b' to boot. (i assume this still works in grub2 but don't know for sure.)

If you don't want to have to do this every time, you'll have to reconfigure grub2. I guess Startup Manager is the tool for that but I really haven't done much with grub2.

---

### Post by ozzynotwood on 2010-10-02
> **decoherence said:**
> You should be able to add nomodeset to the boot line when grub comes up. Recent versions of Ubuntu don't show grub by default. Hold down the shift key while booting to get it back. Some people report that this doesn't work but I think the timing is just picky, so you might have to try it a few times to get it right.

Then type 'e' to edit the default boot line and add nomodeset to the end. Then type 'b' to boot. (i assume this still works in grub2 but don't know for sure.)

If you don't want to have to do this every time, you'll have to reconfigure grub2. I guess Startup Manager is the tool for that but I really haven't done much with grub2.

Holding down shift just make my computer hang just before I get to the "out of range" error, what should I try now?

---

### Post by mörgæs on 2010-10-02
It would be easier for people to help you, if you posted everything in the same thread.

---

### Post by ozzynotwood on 2010-10-03
Problem solved using this guide after 10 hours of searching:

[http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/](http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/)

---

### Post by decoherence on 2010-10-03
> **ozzynotwood said:**
> Problem solved using this guide after 10 hours of searching:

[http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/](http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/)

I'm glad you got it fixed and thanks for posting your solution! I'll be bookmarking that page. Consider marking this thread [SOLVED]

---

### Post by ozzynotwood on 2010-10-03
> **decoherence said:**
> I'm glad you got it fixed and thanks for posting your solution! I'll be bookmarking that page. Consider marking this thread [SOLVED]

I wanted to do that, how do I?

---

### Post by mörgæs on 2010-10-04
In the Thread Tools-menu.

---

