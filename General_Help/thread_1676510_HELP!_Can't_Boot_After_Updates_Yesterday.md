---
title: "HELP! Can't Boot After Updates Yesterday"
date: 2011-01-27
forum: General Help
---

### Post by onaridge on 2011-01-27
I can't fully boot after restarting after I applied yesterday's updates. I boot to the wallpaper and I see Pidegon starting to autostart (the image of the window is there but it is empty). The menu bar is there but the system monitor window is frozen. There is a 2 inch black space at the bottom of my desktop and no docky. Nothing works. I restarted a few times using the power on/off button, no change. Help!!! I haven't installed anything new other than the updates yesterday, or played around with the system for weeks.:(

---

### Post by marin123 on 2011-01-27
[http://ubuntuforums.org/showthread.php?t=1663916](http://ubuntuforums.org/showthread.php?t=1663916)

xorg update killed it. it happened to me yesterday and once before. it best if you dont update xorg.

---

### Post by onaridge on 2011-01-27
When my copy of Linux was installed the guy hid the grub screen. What do I do to get it back? I can't do any of the things in the other thread.

---

### Post by onaridge on 2011-01-27
control x F1 only gives me a login command line, not sure how to proceed

---

### Post by onaridge on 2011-01-27
Ok I figured how to get to console but when I gave it the sudo aptitude reinstall xserver-xorg xserver-common command, even tho it looks like it reinstalled, nothing has changed upon reboot. I can't access GRUB. Someone please help :-(((

---

### Post by ajgreeny on 2011-01-27
If you press shift once the machine has gone through the POST after the power button at boot-up, you should see a grub menu, but if xorg updates are the problem, that may not help you at all.

However, try to get to the grub menu and then choose an earlier kernel from the list to see if that helps.

---

### Post by onaridge on 2011-01-27
Thank you AJ but the same thing happened in a previous kernel. I also went into the recovery kernel and repaired but that didn't work either. I tried yet an earlier kernel and it wouldn't boot into that at all. I am at a loss as to what to do now. I thought this was the one thing I wouldn't have to worry about by dumping Windows and going to Linux. :-((. If Xorg updates are buggy, why are they updating it?

---

### Post by marin123 on 2011-01-27
did you install proprietary drivers? you need to reinstall the same driver that was installed. i downloaded ati driver from their website and i had to reinstall that again. xserver reinstallation didnt help me.

i guess xorg server doesnt play well with proprietary drivers, thats why updates are buggy. if you dont use proprietary drivers, you wont get into trouble.

when you turn on your computer, hold Shift, that should get you to boot menu.

---

### Post by onaridge on 2011-01-27
Marin no I didn't but now everything works so I did something right, the question is which thing? LOL. I rebooted into the latest kernel after doing all the above stuff and all is well.
The cube and effects don't work but that's ok, I don't need 'em and am just happy all is well. Thanks everyone!!

---

### Post by marin123 on 2011-01-27
you will find out next time you do xorg update :D

enable desktop effects. thats why cube doesnt work.

---

