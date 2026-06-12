---
title: "Startup swap error: Can't login to ubuntu"
date: 2010-01-31
forum: General Help
---

### Post by espressobeanie on 2010-01-31
I am running Ubuntu 9.10 with a kernel version 2.6.14. I have tri-booting in grub 1.97~ between Ubuntu 9.10, Ubuntu 8.10, and Win Vista.

My problem is this: I boot into Ubuntu and a message appears. "Can't mount swap in /dev/sda" followed by more text that disappears so fast, I can't make it out. Then, I get to the login manager. It shows my username, and I enter my password. It disappears and the ubuntu loading bar appears for a couple of seconds. Then I get a black screen for a sec and get dumped back into the login manager with no error messages. I keep trying to get in and it keeps doing this. It's stuck on a loop of some kind and I can't log in.

My setup is as this:

Swap - sda7
Ubuntu 9.10 - sda5
Vista - sda6
Ubuntu 8.10 - sda4

Ubuntu 8.10 doesn't have a swap.

---

### Post by gmargo on 2010-02-01
Try switching to a text-mode alternate console using CTRL-ALT-F1.
Then hopefully you'll be able to login to normal shell.
Stop gdm from the command line with "service gdm stop".
Then hopefully you can fix the swap problem.

---

### Post by sandkernel on 2010-02-01
Try <ctr><alt><F2> - that will get you to a shell. Log in and then sudo su - to root. No edit your /etc/fstab file and comment out the swap partition. Reboot and see if you can log in through gdm at that point.

---

