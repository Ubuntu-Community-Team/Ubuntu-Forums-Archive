---
title: "Ubuntu won't load or display"
date: 2011-08-06
forum: General Help
---

### Post by Jo.Buntu on 2011-08-06
I just did a fresh install of 11.04 on a brand new HDD. The install went fineup until a restart was needed and the OS tried loading. I got no UI, just an error message. I went to reboot and after the MOBO's splash screen my monitor goes into power save and goes black. How can I fix this?

When I put the install CD in it recognizes that there is already an install of ubuntu 11.04 on the machine. I've tried reinstalling and that didn't help at all. Also, for reference, the "try ubuntu" option from the boot cd works fine.

---

### Post by Jo.Buntu on 2011-08-06
I hope this helps. Here is a photo of the last screen I get to see before It displays nothing. This is before the initial restart.

[IMG]http://img26.imageshack.us/img26/5411/imag0156t.jpg[/IMG]

---

### Post by Wim Sturkenboom on 2011-08-06
Did you try safe (recovery mode)? If you don't get a grub menu at boot, keep <shift> pressed while booting.

What happens when you press <Alt><F7> (usually the console for the GUI) or <ALT><F8> have seen that one sometimes)?
what happens when you press <ALT><F2>.
Do the above once the last lines shows.

And what is your video card?

You more than likely have a driver issue for the video.

---

### Post by Wim Sturkenboom on 2011-08-06
If you can get to a grub menu, you can press 'e' to edit the parameters. There will be a (long) line probably wrapping with *_quiet splash_*. Replace those two words by a single *_nomodeset_* and press <ctrl>x to boot.

What happens?

---

### Post by Jo.Buntu on 2011-08-06
I was able to get into GUI by replacing my xorg.conf file with the failsafe file after getting into a console from recovery mode. Problem is I didn't backup my xorg.conf file. [S]Can someone upload a basic one that I can edit from there? I am using an Nvidia graphics card. I am fairly new at this. [/S]

Also, so you all can have a laugh, I realized the reason that it wasn't functioning properly was the 6-pin wasn't even connected to the graphics card. Lesson learned, don't toy around in your tower drunk. ha

I just made one from scratch and it seems to be working. I'm getting pretty okay at this as far as problem solving and being new goes. :D

---

