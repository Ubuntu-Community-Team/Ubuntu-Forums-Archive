---
title: "Display Problem in Textmode"
date: 2006-03-20
forum: General Help
---

### Post by mithion on 2006-03-20
I have a display problem when i'm using the command line.  I posted a thread a long  while ago and nobody answered this.  So i'm trying again.  Basically, when using the background command line, the screen is shifted downward.  It's hard to explain.  Then, the bottom of the screen is mirrored on top.  The weird part is that in gnome, it's all working flawlessly.  The screen resolution works beautifully.  But in text mode, I have this bizarre problem.  

Here's what my wild guess is on what's causing this problem.  I'm on a laptop with a 13.3 inch widescreen.  From what I've seen, this is an uncommon screen size and form factor.  Gnome being graphically oriented covers a wider array of screen sizes and resolution so has no problem with this.  But whatever software is responsible for the display in linux command line itself, doesn't support that type of screen.  If anybody knows how to fiddle with the parameters of display for the command line, that would be awesome.

---

### Post by Ramses de Norre on 2006-03-20
You could try to set another resolution by adding vga= with an appropriate value as a kernel option in grub.
I have no idea about which values to use though..

---

### Post by schilcha on 2006-03-20
I did encounter the same problem -- I don't really have a solution, just workarounds. The vga=-thing also worked for me. The boot-splash didn't work any longer (afaik, it's only available for 640x480), which I prefer anyways. 

Another workaround that worked on my notebook (1400x1050) was to press the special key that normally turns off the LCD (under win it did). With ubuntu, this key will just turn off the screen just for a second or two. Afterwards the text-console was fine again (and I reclaimed my last two lines).

A third approach (though useless for me in most situations): Don't start X anyways. Without X, textmode was ok all the time. (who needs graphics -- command line is all it takes)

Good Luck!

---

### Post by mithion on 2006-03-21
Ok, I don't have that special key to turn off my lcd on my laptop, or maybe it's just not configured in ubuntu.  But I am interested in trying the vga= thing.  I'm pretty new to linux.  How does this work?

---

### Post by schilcha on 2006-03-21
The vga parameter needs to be passed to the kernel at bootup. You can specify such parameters in the file /boot/grub/menu.lst.
```

sudo gedit /boot/grub/menu.lst

```
Somewhere down the file, you'll find lines like this:
> 
title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet nosplash 
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot

Add the vga-parameter to the end of the line starting with kernel, like this:
> 
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet nosplash vga=0x31A

Here's a list of valid parameters to vga (taken from /usr/src/linux-source-2.6.12/Documentation/fb/vesafb.txt)
```

    | 640x480  800x600  1024x768 1280x1024
----+-------------------------------------
256 |  0x301    0x303    0x305    0x307
32k |  0x310    0x313    0x316    0x319
64k |  0x311    0x314    0x317    0x31A
16M |  0x312    0x315    0x318    0x31B

```

DO NOT change all your kernel-lines right away. For me some vga-values did not work. You might end up with a non-booting system. I recommend to 
*) copy one of the boot-option-blocks
*) give it a new *title* (e.g. vga-test)
*) add the vga-parameter to the kernel-line of this copied block

Then reboot your system and select the newly created entry from the boot-menu.
If everything works fine, you can add this vga-parameter to all (non-rescue) boot-blocks.

BTW, a kernel-update will reset all kernel-parameters. To keep your handcrafted parameters, add the vga parameter to another section in your menu.lst-file, just like in the following example:
```

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet nosplash vga=0x31A

```

Good Luck!

---

### Post by mithion on 2006-03-21
Well, it worked.  Thank you so very much.  I've had this problem since October so I'm glad it's finally solved.  My splash screen is straight and my command line is finally fitting correctly in the screen.  Again thank you \\:D/

---

