---
title: "Crash for no good reason"
date: 2010-12-04
forum: General Help
---

### Post by Rjm555 on 2010-12-04
Well i bought a zotac zbox and I'm really cheap so I thought I'd give ubuntu a try. I uploaded it to my seagate USB drive and loaded it and whatnot, it all worked perfect and I loved it. So I had it for about two weeks maybe three, I loved open office and the interface, it was lightning fast too, the only thing I changed was instead of firefox I used chrome but thats a personal thing. Then one day two or three weeks in, I had been off for about a week, so I turned it on, booted up, no problem. I went to open chrome, it came up but said there was no Internet. I thought "okay that's weird I can see the wifi is on.?" so I looked on the status bar and it said that wireless was disabled, I didn't know that could happen, I tried to undo It but couldn't. So I clicked the help button and it came up as a silhouette of the window that was totally white. I shut the help window and tried again, still just a totally white window. I tried a few other things, they all came up white. So I said "okay, it restarts in like fourty seconds so already I've spent too much time" ( I spent too much time as a pc, never shutting down unless absolutely necessary because it takes to long). So I did.

But what makes me angry is what happened next. When it came back on it was in what my research says is "busybox" and won't run but a few of the busybox commands on the Internet that it is supposed to. Here is what it says:

[bunch of numbers I dont feel like typing on my iPod]
[more numbers]---[end trace  1173cbbe314988d0 ]---
killed
mount: mouning /dev on /root/dev failed: no such file or directory
(then it showed the same thing as one line up only instead of /dev it had /sys, then one for /proc
Target filesystem doesn't have /shin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _.  <---- that is the typey thingy ( terminologically challenged much?) i don't know if it will help you but that's what it says


When I try 'help' I only get a few commands I can use, mist don't even do anything.


My thumbs are sore from typing this because I don't have anything to type it on other than my iPod touch, so help is greatly appreciated. Would formatting my drive help? If so how can I in busybox (already tried the fdisk stuff, won't even recognize fdisk is a command)?

Thanks for any and all help guys.

--rjm555

---

