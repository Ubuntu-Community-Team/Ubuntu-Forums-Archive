---
title: "cannot boot into safemode"
date: 2010-01-28
forum: General Help
---

### Post by AnthIste on 2010-01-28
hi there

I have a relatively fresh install of ubuntu 9.10 and decided to do some tweaking. I edited the grub2 menu background and font using /etc/defaults/grub and friends and everything worked fine. I then downloaded startupconfig and changed a resolution (think it was the splash) to the highest supported which was 1600x1200. My monitor runs at 1600x900 natively. After rebooting to check it out, i got a nice custom grub2 menu, but after choosing to boot ubuntu i get a black screen. Okay, change the res back from recovery mode? Nope. I get a blank screen loading recovery mode as well. Which leads me to believe that this is more than just a graphics problem.

I am utterly at a loss about what to do. Any help would be greatly appreciated.

---

### Post by john_spiral on 2010-01-28
boot of the Live CD, mount your local ubuntu disk, undo changes

---

### Post by AnthIste on 2010-01-28
ok tbh i wasnt expecting such a fast reply :P il try that tomorrow when i have time. any idea exactly why it would break the recovery mode as well though? EDIT: if i ran update-grub from the live cd would it be the same as always or do i need to /media/ubuntu/usr/sbin/update-grub (or something similar, I obviously dont have any means to check atm)

---

### Post by john_spiral on 2010-01-28
not sure, looks like loads of people are having lots of fun with grub 2, it may technically be better than it's predecessor but it doesn't seem very user friendly.

---

### Post by drs305 on 2010-01-28
Since we don't have the Grub 2 /boot/grub/grub.cfg file to go on (although via the LiveCD you could mount your system partition and access it or run the [boot info script]("http://ubuntuforums.org/showthread.php?t=1291280")), you can do this:

At the Grub 2 menu, highlight the Ubuntu kernel you normally boot. Press the 'e' key, which will open the menu entry. If you recognize the items you added to the menu, use the arrow keys to move to this section and use the delete key to remove them. Then press CTRL-x to boot.

If you don't see anything in the boot instructions that you changed to effect your resolution, it is likely the problem is not in Grub but in system files used after Grub passes control to the kernel.

---

### Post by AnthIste on 2010-01-29
ok removing splash and quiet from the parameters in the grub menu got me a desktop so I can work from there. seems to be usplash causing the problem. if I fix it completely Il post back here.

EDIT:

A simple
```

sudo dpkg-reconfigure usplash

```
did the trick nicely.

---

