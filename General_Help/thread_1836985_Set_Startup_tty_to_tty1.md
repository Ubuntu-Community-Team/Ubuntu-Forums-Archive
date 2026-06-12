---
title: "Set Startup tty to tty1"
date: 2011-09-01
forum: General Help
---

### Post by Tyler H 0203 on 2011-09-01
By default, Ubuntu switches to tty7 on boot, even when a command line environment is installed. The problem is that, on the command line install, there's no getty started on tty7. So, I want to make it switch to tty1 by default. How can I do that?

BTW, I'm using 11.10, but 11.04 does the same thing. IIRC, this problem didn't exist for 10.10 and before.

---

### Post by papibe on 2011-09-01
Welcome!

AFAIK, 1 through 6 is reserved to text mode. Once connected you can go to the text mode by pressing Crtl + Alt + Fn (1 tp 6) and then login. If you go to session 1 (F1) you'll be on tty1, etc.

To go back to the graphical mode press Crtl+Alt+F7.

Hope it helps,
Regards.

---

### Post by Tyler H 0203 on 2011-09-01
Sorry, slight misunderstanding. When I say "the command line environment" is installed, I mean the command line only version.

I know I can switch, actually, I have to. It's just a small inconvenience I'm trying to fix. I want to make it where it starts to tty1 instead of tty7, because, for me, there's nothing on tty7.

Thanks for the extremely quick reply.

---

### Post by papibe on 2011-09-01
Let me see if I understand correctly. I'm guessing you installed the server version or the minimal install, but you boot into a blank screen and have to switch to text mode using Crtl+Alt+F1 ?

(This just happened to me, that's because I'm having this inkling).

Regards.

---

### Post by Tyler H 0203 on 2011-09-01
Yep. That's it exactly. I installed the minimal install version, because it's for a VM which I plan to use for compiling stuff.

It took the longest time for me to figure out what was going on. I thought the kernel was hanging before it started init or something weird like that.

---

### Post by papibe on 2011-09-01
It's a bug in the install CD. (More info here: [Bug #695658]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658"), [Bug #700686]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/700686"), and [Bug #831752]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/831752")).

To fix it, as explained in Bug #695658:
> (1) Edit /etc/grub.d/10_linux (e.g. "sudo nano -w /etc/grub.d/10_linux") and comment out the line containing "vt.handoff", or change the number from 7 to some lower number. (I tried it both ways; they both worked.)
(2) Run "sudo update-grub" to apply the new configuration.
(3) Reboot. A usable virtual terminal with a login prompt comes up automatically.

Try it out, and let us know how it went,
Regards.

---

### Post by Tyler H 0203 on 2011-09-01
YES!!! It works! Thank you!

As conceited as it may make me sound, I actually had an idea it could be a kernel option, seeing as I couldn't find anything related to it in init.d/. I just had no idea what such an option would be called...

---

### Post by papibe on 2011-09-01
Glad you solved it :P Mark the thread 'solved' when you have the time.
Regards.

---

