---
title: "Terminal Text (not in xterm) scrolls off screen"
date: 2006-01-21
forum: General Help
---

### Post by damonkohler on 2006-01-21
Whenever I'm in a real terminal, i.e. tty1, and the text reaches the bottom of the screen, I can't see the last few lines any more. It's very odd and rather annoying. The whole buffer gets messed up once that happens and even logging out of the terminal won't fix it. Help me please?

Update: Ctrl-L gets it back to something usable but apps like man and emacs freak out and don't scroll properly.

---

### Post by damonkohler on 2006-01-28
Does anyone have any ideas here? I think it has to do with the framebuffer. Bascially there is a blank space about 5 lines long at the bottom of the screen when I'm in a virtual terminal. The text scrolls off into there and it can't be seen. Pressing enter a bunch of times scrolls it up into the space that can be seen and pressing Ctrl-L clears the screen and lets me keep entering commands.

---

### Post by damonkohler on 2006-02-10
Finally found some information about this. It's a framebuffer issue. Does anyone know where to find the framebuffer configuration options they're talking about? It would be nice not to have to disable the framebuffer with nofb.

[http://www.techimo.com/forum/t160756.html](http://www.techimo.com/forum/t160756.html)

---

### Post by damonkohler on 2006-02-10
So I modified /boot/grub/menu.lst and replaced all the instances of "splash" with "nosplash" and that did the trick. I don't get the leet bootup graphics though now :(

---

### Post by damonkohler on 2006-02-13
Fixed it by adding vga=791 to the kernel boot options and doing the vesafb.ko fix here:

[http://www.ubuntuforums.org/showthread.php?t=83151&highlight=vesafb.ko](http://www.ubuntuforums.org/showthread.php?t=83151&highlight=vesafb.ko)

---

### Post by ubuntumaneh on 2006-02-13
Can't you set framebuffer in xorg configuration? Try it:

sudo dpkg-reconfigure xserver-xorg

---

