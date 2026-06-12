---
title: "My Terminal is HUGE!"
date: 2009-07-10
forum: General Help
---

### Post by srilyk on 2009-07-10
And no, this isn't some ad for natural supplements ;)

For some strange reason, my terminals (ctrl+alt+f1-f4) are HUGE. The text size is large, and it spills off the bottom and possibly side of the screen.

Basically, ubuntu seems to think my screen is two or more pages long. I rarely mess with the regular terminal as I tend to ssh into this box, but on occasion I have need to access the terminal and it's a huge pain to have to type "clear" after I login or type two or three commands, just so I can see the information I'm typing.

Google hasn't turned up any information with my searches, so I thought I'd ask here...

Any help?

---

### Post by fela on 2009-07-10
Ok:

```
sudo apt-get install hwinfo
```

then,

```
sudo hwinfo --framebuffer
```

If your desired resolution in 24 bit doesn't come up, you're _probably_ and to my knowledge gonna have to put up with the big terminals. But if it does, note down the 0xXXX code to the left of it.

Now, edit /boot/grub/menu.lst as root, and find the bit where it says 'title Ubuntu...etc)', and in the kernel line below the title line, put 'vga=0xXXX' (XXX being the code you found earlier). There's probably already a vga=xxx, if so just change the 0xXXX. Then reboot and your terminals _should_ be fixed. If the terminals are all fubar, or for some reason you cannot boot because of it, just boot into recovery mode (or use a different terminal), edit /boot/grub/menu.lst: ```
nano /boot/grub/menu.lst
``` and delete that vga line.

---

