---
title: "grub trashed - error no 17 (argh)"
date: 2006-03-27
forum: General Help
---

### Post by dotdot on 2006-03-27
hello - I wonder if anyone can give me a solution to this .. (major) problem ..

..I boot up - only to have error with grub

Error  17

..I've booted off install disk - initiated rescue at the boot prompt

now I've managed to mount my / fs and have traversed to /boot/grub

..looking at my config files everything looks as it should - but obviously something is not right....

Can someone shed some light on what I can do to get out of this - hole.

..

---

### Post by justleen on 2006-03-27
did you run grub-install while in rescue mode?

---

### Post by dotdot on 2006-03-27
have managed to mount up /

grub-install /dev/hda fails with
The file /boot/grub/stage1 not read correctly...
....
when i now go into grub ( expecting to see grub> )
.. it errors with 
Error opening terminal:bterm

...any ideas ?

---

### Post by sYs^ on 2006-03-27
I hope it'll help

[http://ubuntuforums.org/showthread.php?t=145481&page=2](http://ubuntuforums.org/showthread.php?t=145481&page=2)

---

### Post by dotdot on 2006-03-27
just for ref - still no joy.

1/ booted totally from live cd
2/ went into grub - found stage 1
3/ reset root and setup as per..
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

reboot - still no joy.

...will investigate Using the Unofficial "Linux Super Grub Disk"

later... 


what a story...

---

