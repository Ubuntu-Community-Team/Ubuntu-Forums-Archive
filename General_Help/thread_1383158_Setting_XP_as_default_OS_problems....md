---
title: "Setting XP as default OS problems..."
date: 2010-01-16
forum: General Help
---

### Post by JoeyTrez on 2010-01-16
Ok so I'm attempting to put Windows XP as my default OS instead of Linux.
I use the terminal and add the sudo gedit /boot/grub/menu.lst command.
It just opened up Tomboy with the text that I entered in the terminal.
So in other words, that thing where I have to change the number to put XP as default doesn't come up.
My friend tried to help me with some other commands but no dice on that either.
Can you guys help me as to how I can fix this or a separate command that could work?
As usual, any help would be greatly appreciated. Thanks a bunch.
-Joey.

---

### Post by lukeiamyourfather on 2010-01-16
What version are you using? If using Karmic (9.10) that file might not be used anymore because of the new version of GRUB (the bootloader). There's an application to manage the startup options in GRUB, I think its called Startup Manager or something like that (don't have Ubuntu in front of me). It'll allow you to change the default option and other tweaks from a GUI that works with the new GRUB. Cheers!

---

### Post by JoeyTrez on 2010-01-16
Oh......man.
Thanks SO much.
Worked like a charm

---

