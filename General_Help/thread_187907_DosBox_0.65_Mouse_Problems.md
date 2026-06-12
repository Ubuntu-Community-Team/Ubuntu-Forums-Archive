---
title: "DosBox 0.65 Mouse Problems"
date: 2006-06-03
forum: General Help
---

### Post by dualtone on 2006-06-03
Hi!

I'm a newbie, using Dapper, having some trouble with DosBox 0.65.

After installing fglrx and using 'sudo dpkg-reconfigure xserver-xorg' to set it as my graphics driver (using a Dell Inspiron 9300 with an ATI Radeon M300) i seem to have inadvertently done something to my mouse settings.

The problem only affects DosBox --
When running software through it that uses my mouse, the cursor immediately jumps to the top left corner and gets stuck there.

The mouse settings in DosBox itself have not been changed, so I can be fairly sure that using xserver-xorg was the cause.

Any suggestions?

Thanks!

---

### Post by csurigao on 2006-06-23
Have you tried using CTRL+F10 to set the mouse in the dosbox window??

---

### Post by dualtone on 2006-06-25
Yep. No joy :-(

---

### Post by pixel :-) on 2006-08-14
i had same problem with qemu, same driver(fgrlx).I finally found this
[http://wiki.clug.org.za/wiki/QEMU_mouse_not_working]("http://wiki.clug.org.za/wiki/QEMU_mouse_not_working")
before you start dosbox just type :KS 

export SDL_VIDEO_X11_DGAMOUSE=0

thers also a problem with the special keys, if you no how to fix that ?

---

### Post by adamc55 on 2006-08-14
How does one get DosBox 0.65? The one that synapic installs is 0.63, and when I try to compile from the tarball it complains about not finding sdl-config...

---

### Post by adamc55 on 2006-08-14
Nevermind... in the hope that it will help someone else: you need to install libsdl1.2-dev.

---

### Post by xy77 on 2007-03-20
After installing feisty I had the same problem, only it was the bottom right corner. I solved it by booting from the feisty herd 5 cd and copying the xorg.conf to my system. A compare might help. I wasn't able to localize the problem, but it works finally.

- David (xy77)

---

