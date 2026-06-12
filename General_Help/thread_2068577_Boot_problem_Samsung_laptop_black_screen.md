---
title: "Boot problem Samsung laptop black screen"
date: 2012-10-09
forum: General Help
---

### Post by sysone on 2012-10-09
On a Samsung laptop with Ubuntu 12.04.1 64  this is the correct start-up:    Start --> Samsung logo -->Linux 3.2.0-31-generic -->blue screen -->black screen --> Ubuntu logo -->enter password -->Ubuntu site.

But about 50% of the time it stops at the 'black screen' and hangs. Ctr+Alt+Del does not work.  Only hard shutdown works at that time.

However when one starts with 'Previous Linux Versions' i.e. 3.2.0-30-generic , everything works fine.

The owner has gotten used to using Previous Linux Versions.

I didn't really know what to do. Tried Grub Repair and also tried to boot from a USB to reinstall grub. Problem persists.

Thanks

---

### Post by dino99 on 2012-10-09
remove "splash" from the boot line (for testing) (hit E on the grub line to edit it, do the modif, then ctrl+x to boot)
or :
sudo gedit /etc/default/grub
(to set the change permanent)

sudo update-grub

if that does not work, you then might need testing some boot option
( google around "ubuntu boot option" )

and of course, the logs are usefull to know what is wrong. Check both: /home/youruser/.xsession-errors (ctrl+h to unhide it) and /var/log/

---

### Post by sysone on 2012-10-11
worked well

Thanks

---

