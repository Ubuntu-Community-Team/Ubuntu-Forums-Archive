---
title: "Reboot to specific partition"
date: 2010-04-18
forum: General Help
---

### Post by lduperval on 2010-04-18
Hi,

When I used to ride with Gentoo, there there was a reboot option that allowed you to specify what to reboot. So if I needed to reboot to windows, I selected the "Windows" partition and it would reboot in Windows, without me having to select it from the GRUB menu.

Does this exist for Ubuntu? If so, where?

Thanks,

L

P.S. I'm on Lucid

---

### Post by quixote on 2010-04-19
Um, I think the short answer is "No."  What's the reason for avoiding grub?  Maybe there's some other workaround for whatever it is you need to do.

---

### Post by cdaringe on 2010-04-19
yea, not yet!
subscribing to thread due to curiosity...

---

### Post by drs305 on 2010-04-19
I am not aware of anything like that at the moment, but it wouldn't be too hard to accomplish with scripts.

*Puts on thinking cap...*

You could easily achieve this using Grub 2's flexibility. 

You would create a script and use the exact title of the menu entry so that its position in the list doesn't effect the outcome. Then it would only be a matter of invoking a script, perhaps using *zenity* so you have a GUI interface, to insert the correct title into /etc/default/grub's "DEFAULT=" line and run update-grub to incorporate the change.

You would use sed or another command to edit the "DEFAULT" line and insert your desired next boot OS. If you made a /etc/grub.d/06_custom file so it's contents were always at the top of the list you could even use numbers instead of titles, since they would not change menu positions unless you manually edited the 06_custom file.

Of course, you could also simply use "startupmanager" to set the default OS for the next boot. Startupmanager still works in Grub2 for setting the defaults OS.

---

### Post by lduperval on 2010-04-19
Thanks for the tips. This is all quite involved, as I can see. In Gentoo it was just there and honetsly, I was surprised when I didn't find it in Ubuntu when I switched.

The reason I want this is because when I reboot, I don't want to sit in front of the screen and wait for the boot menu. I've missed it once too many so I decided to ask the question.

I'll ask on the Gentoo forums what they do and I'll come back and report when I find something interesting.

L

---

### Post by drs305 on 2010-04-19
> I'll ask on the Gentoo forums what they do and I'll come back and report when I find something interesting.

Please do. And if it's an applet of some sort, provide the name and perhaps we can find the equivalent over here. One of the beauties of linux is someone has probably already solved your issue, we just haven't located it yet.

---

### Post by marshmallow1304 on 2010-04-19
I just happened to be poking around in the grub documentation just now.  You might find hints in the man page for grub-reboot.


Edit:  It doesn't seem to work for me.  I did
```
sudo grub-reboot 5
sudo reboot
```
to no effect.  Maybe someone else can figure it out.

---

### Post by drs305 on 2010-04-19
> **marshmallow1304 said:**
> Maybe someone else can figure it out.

Glad you brought that up!

There were a few problems with it early on and I'd forgotten about grub-reboot. I don't think it still works consistently in Grub 1.97~beta (Karmic).

The good news is that I believe it is working in 1.98 (Lucid). A fix was committed to various bug reports and I've just successfully tried it.

To get grub-reboot to work, make sure you have *GRUB_DEFAULT=saved* in /etc/default/grub and run update-grub.  

When you run "sudo grub-reboot" you can use either the menu number (starting from 0) or an exact quote from the /boot/grub/grub.cfg file. The quote would be everything between the quotation symbols on the menuentry line.

If I were to use this regularly, I would either use the exact quote or build a 06_custom file so I know the numbers would not change when a new kernel arrives. G2 is supposed to be smarter about menuentry positions but I would stick with a manually-edited custom file.

---

