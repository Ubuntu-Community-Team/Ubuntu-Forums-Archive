---
title: "Plymouth usually boots in low res text mode"
date: 2010-07-05
forum: General Help
---

### Post by chickencaesar on 2010-07-05
Most of the time instead of a pretty graphical splash I'm getting a small low res text version of the boot screen squeezed into the top left hand corner of my display on my laptop with Intel GMA4500 graphics.

Originally I was getting a blank screen with the Plymouth splash only appearing a couple of seconds before log-in. Adding FRAMEBUFFER=y to /etc/initramfs-tools/conf.d/splash got rid of the blank screen but at the expense of the ugly boot screen mentioned above. To confuse matters, now and again (roughly 1 boot out of 10) I am getting a perfect graphical boot. I've tried reinstalling Plymouth and using different boot themes but to no avail.

Any ideas?

---

### Post by chickencaesar on 2010-07-12
For the interest of anyone with the same problem, I've found a workaround. Add the line 'sleep 1' to the end of the script in /usr/share/initramfs-tools/scripts/init-top/framebuffer and run 'sudo update-initramfs -u'. If this improves but does not entirely solve the issue, try 'sleep 2' etc until the problem disappears.

---

