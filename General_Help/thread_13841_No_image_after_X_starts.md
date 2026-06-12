---
title: "No image after X starts"
date: 2005-02-03
forum: General Help
---

### Post by frontline3k on 2005-02-03
Hi.
I wanted to try Hoary Live CD and I have a problem: after X starts, there is no image on the screen. I tried to switch to another tty and ... no luck.
The only way to exit is pushing the little reset button.

Something like this was happening when I installed Warty, when X was auto-configured for a resolution higher than my monitor specs, but after installation of the nvidia driver and tweaking xconfig, the problem was solved.

Any ideea ?

Specs:
MB: Intel 865 PERL
Video: Leadtek WinFast A360 (FX 5700)
Sound: MB integrated and Creative Audigy.

---

### Post by alastair on 2005-02-03
[QUOTE=frontline3k]Hi.
I wanted to try Hoary Live CD and I have a problem: after X starts, there is no image on the screen. I tried to switch to another tty and ... no luck.
The only way to exit is pushing the little reset button.

Something like this was happening when I installed Warty, when X was auto-configured for a resolution higher than my monitor specs, but after installation of the nvidia driver and tweaking xconfig, the problem was solved.

Any ideea ?

Specs:
MB: Intel 865 PERL
Video: Leadtek WinFast A360 (FX 5700)
Sound: MB integrated and Creative Audigy.[/QUOTE]
 How long did you wait?
Did an X cursor appear at all?
Did you try CTR:+ALT+BACKSPACE?

I can't remember, but there's probably a way to boot in text mode. Try that and use "startx".

---

### Post by frontline3k on 2005-02-04
> How long did you wait?Long enough ...

> Did an X cursor appear at all?No ...

> Did you try CTR:+ALT+BACKSPACE?Yeah, still the black image.


I'll try tonight with a different monitor.

---

### Post by UbuWu on 2005-03-05
I have exactly the same problem...

When I select the 1280x1024 with FB option in the boot menu, the problem is gone though, but then I don't get a resolution of 1280x1024 but 1024x768. When I try to correct that in gnome, the system suddenly reboots.

---

