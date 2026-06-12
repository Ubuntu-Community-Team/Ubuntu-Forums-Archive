---
title: "keyboard doesn't work after suspending to ram"
date: 2009-09-09
forum: General Help
---

### Post by khatat on 2009-09-09
hi all
 I have just installed kubuntu 9.04 on my laptop. when i suspend system to ram it's ok but when i resume i can't type anything and i have to restart
 any idea? for example how can i enable keyboard through apmd? is this possible or ...
 thanks for your help and sorry for my bad language.:lolflag:

---

### Post by P4man on 2009-09-09
You could try booting with this kernel option:

```
i8042.reset
```

Use this how-to
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

But instead of adding "vga=771" like in their example add "i8042.reset".
If that helps, you can make this permanent by modifying your grub menu (see same page, next section)

---

### Post by khatat on 2009-09-09
:(
thanks for your reply but it didn't help me?
how can i enable/disable keyboard through kernel? i mean if i know how can i enable my keyboard i can enable it when resume by apmd.
thanks again

---

### Post by P4man on 2009-09-09
Im not sure we understand each other. what I suggest is a workaround that will make the kernel reset the keyboard controller upon initialization and reset (which I guess also happens when resuming). By setting that, its possible you can suspend and resume without problems. To test, you have to reboot, add that setting in grub (see my link), then boot ubuntu, and try suspending / resuming. If it doesn't help, there are few other switches we can try

---

### Post by khatat on 2009-09-09
hi
i understood you completely i added i8042.reset and booted kernel with this option but no result i still have that problem and thus i have to restart system and it is very bad for my laptop
please if you know any other option let me know.
thanks a lot

---

### Post by P4man on 2009-09-09
Why is it bad for your machine? Surely you can do a clean reboot with the mouse only? Anyway, here is another possible fix:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99755/comments/34](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99755/comments/34)

---

### Post by khatat on 2009-09-09
i will kill my self
that approach didn't work oh my god :confused:
meanwhile if said restarting machine was bad i meant frequently restarting or shutting down machine can be harmful for laptop and instead of shutting down it's better to standby that is my problem  ](*,)](*,)

---

### Post by Jugantor on 2009-09-24
I think if you use 
**atkbd.reset **

instead of 
i8042.reset, at the said location,

your problem gets fixed. Atleast it got fixed for me. 

and FYI: upon using i8042.reset, the only change that I noticed was that my desktop gets visible after i resume from suspend, although it does display a window asking for password in front of it.

Hope that helps.

-- Jug:guitar:

---

