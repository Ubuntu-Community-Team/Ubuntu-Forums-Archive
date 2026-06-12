---
title: "fsck 12.04 64bit"
date: 2012-08-06
forum: General Help
---

### Post by MikeCyber on 2012-08-06
Hi
then and when ubuntu boots with read only fs. While rebooting it hangs. Same with the rescue boot.
Luckily I've also 10.4 32bit to boot and can do a fsck, which helps.
What's wrong here?
Thanks

---

### Post by oldfred on 2012-08-06
Was there any abnormal shutdown either power failure or program hang that made you force shutdown with just power off? Always use REISUB in those cases anyway.

What does Smart Data in Disk Utility say about drive. Any issues?

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by MikeCyber on 2012-08-06
Did that but couldn't see anything unusual.

I only happens from time to time...booting now with grub terminal mode, without splash, to see what's going on.

Most annoying is that I need another OS to fix/reboot. I'll report back when it happens again, but usually this takes a week or longer.
Thanks

---

### Post by oldfred on 2012-08-06
You can look into log files to see if something is reported. Not sure for this type of error. Boot errors (maybe shutdown?), I look in dmesg. But there are many log files for different things.

---

### Post by MikeCyber on 2012-08-13
Without splash, I now had the option to fix errors, which I probably didn't have with splash? Hence the read only mount?
Anways fixing helped this time, still need to check next time the logs.

---

### Post by MikeCyber on 2012-08-22
Now it was triggered by google Chrome. I believe it was the same last time...

---

