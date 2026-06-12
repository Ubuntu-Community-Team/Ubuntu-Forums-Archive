---
title: "Grub2 Splash Screen"
date: 2010-11-18
forum: General Help
---

### Post by adv88 on 2010-11-18
Hello guys,
I have installed backtrack4 on my laptop with windows7, and installed grub2...

I am having a problem on showing a splash screen
I don't have a splash screen that shows neither on grub2 nor grub legacy

I have searched too many tutorials, but I don't know what's the problem, because all of them shows how to change the splash image, but don't mention anything about enabling it.

Note that the live cd loads an image.... So I don't think it's my vga or something.

Can anyone help me on this issue?

---

### Post by ajgreeny on 2010-11-18
I have no idea which tutorials you have seen, but I know this method works as I have used it in the past.  I don't bother any more as grub only shows for one second, just to make sure I can see it when needed to boot one of my other less used linux distros.

Have a look at Section 8 of [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275).
EDIT:
A second thought:  Do you really mean a grub splash image or are you asking about the Plymouth boot splash of purple background, the word "ubuntu" and five animated spots beneath?  If that is your problem, there are many bits of info available, but you need to look at "plymouth display" as your search term.  That is _not_ grub.

---

### Post by drs305 on 2010-11-18
Look in Section 8. If you don't understand something in the link *ajgreeny* gave you just ask here.

---

### Post by adv88 on 2010-11-19
Hello, thank you for the reply.
In fact, I have version 1.96,
the problem was with the resolution which was set by previous versions.
I changed the resolution and everything worked fine.
thank you

---

