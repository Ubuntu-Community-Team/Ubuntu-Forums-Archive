---
title: "Problem with tty terminal resolution"
date: 2006-04-14
forum: General Help
---

### Post by JonoF on 2006-04-14
Hi there,

I had been running Ubuntu 5.04 for a few months prior to today with no problems. Today I repartitioned everything and did a clean install of Ubuntu 5.04 (previously was dualbooting WinXP, which I never used on this machine, so I wanted to get rid of XP and give myself more hard disk space to play with in Linux). 

Beforehand, the tty terminals (is this what they are called? when I press Ctrl+Alt+F1 through 6...?) all had a normal font size/resolution, as did the bit which tells me what's happening while Linux is loading up.

Now however, when I go to the tty terminals, it has a very low resolution, and is also offset to the left. 

For good measure, I upgraded to Ubuntu 5.10, but this didn't fix anything - never hurts to try such measures though aye... I searched around on this forum a bit, and found a problem similar to this one, where it was recommended to add a line 'vga=771' or something to that effect in /boot/grub/menu.lst. This also did not help!

Any suggestions? If anything I've written isn't clear I will try to elaborate - I know I have used some extremely technical terms such as "the bit which tells me what's happening while Linux is loading up" :mrgreen: 

Cheers
Jono

EDIT: D'oh!!! Changing the menu.lst file does in fact work! Was just a matter of checking that I had written the 'vga=...' statement on the correct line ](*,)

---

