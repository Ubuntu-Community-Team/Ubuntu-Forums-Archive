---
title: "Start Up taking an unsually long time"
date: 2009-07-22
forum: General Help
---

### Post by redsky1302 on 2009-07-22
Hello! I've been using ubuntu linux for quite awhile on my laptop and desktop.  One of the things which I've noticed is that on my laptop, the system tends to get stuck at the "Starting Up" screen (the one that appears immediately after GRUB, but before the status bar) for a rather long time (20 seconds).   While 20 seconds isn't an exceedingly long wait, compared to my older desktop which skips past this screen in a around 2 seconds, something doesn't seem to be right.  Is there anyway which I can check what's wrong? Thanks in advance for any advice :)

---

### Post by redsky1302 on 2009-07-22
Has anyone any advice for me?  Just to add some info, I'm using an HP pavilion dv4.

---

### Post by Strongman332 on 2009-07-23
do you have a web cam built in. i have noticed that they can add to the boot time

---

### Post by redsky1302 on 2009-07-23
I do have a webcam built in, but I don't think that is the problem. The part that takes the exceptionally long time is not the ubuntu splash screen with the status bar, but the screen before that says what partition it is booting off with the the message "Starting Up". Is there anyway I can enable a non-quiet version of this screen to see what the problem is?

---

### Post by unutbu on 2009-07-23
[list]
[*] To see more messages while booting up:

[list]
[*] Boot the machine
[*] Get to the GRUB menu
[*] Press 'e' to edit the GRUB boot line
[*] Go to the end of the "kernel" line and remove the word "splash", then press Enter
[*] Press 'b' to proceed with the boot
[/list]

The above is a one-time change. The next time you boot, the splash screen will be back.
There is a way to make the change permanent by editing /boot/grub/menu.lst; ask if you want more details.

[*]Also, while booted into Ubuntu, you may want to look at /var/log/dmesg and /var/log/messages and /var/log/syslog. One of these files may provide a clue as to what is taking so long.

[*]Finally, if you install the bootchart package you can generate a chart of what programs are running when and for how long during the boot process. (See [http://ubuntuforums.org/showthread.php?t=531453](http://ubuntuforums.org/showthread.php?t=531453) for examples of what this looks like). To set this up:

[list]
[*] Install the bootchart package
[*] Reboot
[*] Look in /var/log/bootchart for the .png file.
[/list]
[/list]

---

