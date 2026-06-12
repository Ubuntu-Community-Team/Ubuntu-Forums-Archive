---
title: "Booting troubles: /dev/disk/.... does not exist"
date: 2009-12-03
forum: General Help
---

### Post by windfix on 2009-12-03
Yesterday, I began installing a Fedora 12 virtual machine in Virtualbox.  I aborted because it started talking about wiping /dev/sda which I didn't like, and the VM was just for curiousity.  I completed other work and shut down normally.

This morning, I get just past Grub and the ubuntu logo and the screen goes black.  When I hit anything I get:

"Gave up waiting for root device" (plus some language on common issues which I did not understand).

Followed by "Alert! /dev/disk/by-uuid/8842a3b0-be00-4927-b837-9abbe269b924 does not exist.  Dropping to shell."  then "Busybox v1.13.3 built in shell" with a $ prompt.

Help!?

This is a Karmic 9.10 installation, dual booting with XP via Grub (which still works).

---

### Post by etnlIcarus on 2009-12-03
The /dev/sda the Fedora installer was talking about was the virtual disk created by virtualbox. It's a file in your ~/.Virtualbox directory. It's highly unlikely that your current troubles have anything to do with Virtualbox.

---

### Post by windfix on 2009-12-04
OK, makes sense, and I'll try the VM creation again... but to the boot problem, anyone?

Oddly, I attempted twice with same results, booted once to recovery mode - but didn't know what to do from there, once to XP, and then Ubuntu booted normally.

On the next boot attempt... same problem as previous.

---

### Post by etnlIcarus on 2009-12-04
On that, I've got fewer ideas. Perhaps boot from the Live CD, open a terminal and run *fsck*.

---

### Post by windfix on 2009-12-04
Thanks.  I did that ("sudo fsck /dev/sda1" which I verified is my "/" partition) All it said was the file system was clean.  I expected it to do a long checking process, like it does occasionally on startup... but it only took a second.  Is there a different command I should have used?

Also, I tried upgrading to Grub2, hoping it would automagically fix itself in the process, but the problem persisted (intermittently).

Then I followed some instructions to make Grub2 load the "Linux drive using the absolute drive path and not its UUID"; by doing this -

[I]Open /etc/default/Grub. Uncomment the following line:

GRUB_DISABLE_LINUX_UUID=true

Run update-grub in your command line to update your Grub configuration. Now reboot your system. [/I]

Next boot worked... so I will try it another day or so and see if the problem persists.  Does that absolute drive path present any issues?

---

### Post by windfix on 2009-12-06
Another workaround I discovered was to boot with an older kernel from grub.  Now that 2.6.31 has been released and installed, the issue seems to have disappeared.

---

