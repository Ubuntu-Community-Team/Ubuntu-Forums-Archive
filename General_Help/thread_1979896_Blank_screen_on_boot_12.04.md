---
title: "Blank screen on boot 12.04"
date: 2012-05-14
forum: General Help
---

### Post by vita on 2012-05-14
Hi, 

I have a problem with starting up Ubuntu 12.04 x86. I've upgraded 20 days ago from 11.10 and everything was working up until today and now I can't log into the system, it freezes with the blank screen during the startup.

There are no log files on the system (I've checked with live cd all log files and even enabled bootlogd logging but still nothing)

In addition, I can not use ctrl-alt-f1 to get to the terminal and not event ctrl-alt-delete to reboot the computer.

I've tried grub-install from live disk (with proper root-directory) and also to chroot live system and then to run update-grub but still no change.

My system was up 4 days and during that time I've installed the indicator-applet that I was missing after the update. Now, the only one strange thing with the system was that I could not enable/disable the wi-fi network from the indicator tray, and I needed to open up the terminal and run /etc/init.d/network-manager restart. I thought that if would fix after the restart but it wont start at all. :(

I have HP 2530p notebook with Intel integrated graphics.

I've checked the forums and all existing messages are either about hangs after the update or some occasional problems with system hanging....

---

### Post by vita on 2012-05-14
[FONT=Arial][SIZE=1]Found a solution.

The problem was with initramfs.


First, when the grub starts pres 'e' to edit the grub entry and remove all the options on the line that starts with linux after 'ro' (vga=xxx, quiet etc..) and add nomodeset. Press ctrl-x to boot...After that I've finally found the error message

***"***[/SIZE][/FONT]***[FONT=Arial][SIZE=1]Unable to mount root fs on unknown-block(0,0)"[/SIZE][/FONT]***[FONT=Arial][SIZE=1]

after that this helped
[http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0](http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0)
[/SIZE][/FONT]

---

