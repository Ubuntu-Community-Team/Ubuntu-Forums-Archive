---
title: "Frequent kernel panics while using Firefox"
date: 2010-12-05
forum: General Help
---

### Post by rbock on 2010-12-05
Hi,

since a few weeks I am observing kernel panics (caps lock and scroll lock blinking) when using firefox. Sometimes I they occur after a few seconds, sometimes I browse for hours without problems.

It seems I can increase the chances for the kernel panic to occur by opening a page with animations and then scrolling while the animation is still being initialized.

Since the problem occurs in X, I see nothing on the console, obviously. I tried 

ALT SysReq  R S E I U B

which stopped the blinking but did not reboot. I am not good at reading /var/log files and haven't found good hints there, yet.

Ubuntu 10.04, 64bit
Kernel 2.6.32-26-generic
AMD Athlon(tm) 64 Processor 2800+
Firefox 3.6.12

What can I do to diagnose the cause of the kernel panic?

Thanks and regards,

Roland

PS:
I ran memtest86+ for several hours, no errors.

PPS:
If another forum would be better suited, please let me know

---

