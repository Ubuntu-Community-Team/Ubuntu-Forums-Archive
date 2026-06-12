---
title: "Scrambled screen. How do I fix this?"
date: 2010-05-22
forum: General Help
---

### Post by webkris on 2010-05-22
[B]Scrambled login screen and terminal screen.
I'm using LTSP on Ubuntu 10.04[/B]
This is on a brand new WYSE C10LE tested with several monitors.
HOW DO I TROUBLESHOOT THIS??
Remember the xorg.conf is all made on the fly and stored in the LTSP directories. So editing the servers xorg is doing nothing.
There is some documentation at the end of the LSTPManual.pdf that talks about xorg and chroot and dual monitors - but I just don't know where to start...

*(side note - I have tested this image FINE with an old WYSE x150SE thin client and a VirtualBox net boot. So I know it works!)*

[IMG]http://planetkris.com/misc/LTSP_Ubuntu_scramble.jpg[/IMG]

***I hit CTRL-ALT-F1 and instead of text - I get this...***

[IMG]http://planetkris.com/misc/LTSP_Ubuntu_term_scramble.jpg[/IMG]

- Kris

---

### Post by finlost on 2010-05-22
Check your video drivers

---

### Post by webkris on 2010-05-23
Oh yes... So simple... :|
So - I'm on a LTSP server - Is there a guide or some suggestions for this?

This is a PXE boot system, not a "standalone PC".
Further thought out suggestions would be appreciated.
- Kris

---

### Post by voipmaster on 2012-08-16
You ever figure this out? I've got the same thing.

---

### Post by utnubuuser on 2012-08-16
On a PXE boot system, do you have the option to give the kernel boot-paramaters?

ie, on a normal machine, you can change the boot-parameters at the grub screen by pressing "e".

Normally you'd wait to get to the grub-menu, then scroll to the relevant "linux" line, use the arrow keys to navigate to the end of the boot-parameters line and add/ change whatever special parameters are required.

ie: on my machine, which has an older ATI card,  I use the 'nomodeset' parameter to prevent the above shown graphics corruption.

I don't know what PXE is however, so I can't give you any more specific instructions.
Though I'm pretty sure that if you can figure out how to change the boot parameters, you'll get a working graphics solution.

---

### Post by overdrank on 2012-08-16
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

