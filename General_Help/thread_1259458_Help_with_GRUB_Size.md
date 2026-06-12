---
title: "Help with GRUB Size"
date: 2009-09-06
forum: General Help
---

### Post by kyle2595 on 2009-09-06
Hi, on my computer, the GRUB Bootloader is shown in the very center of the screen with about 3 to 4 inches of blackness between GRUB and the edge of my screen. On my friend's computer with GRUB, it takes up the whole screen. Is there a way that I can change the size of GRUB so that it will take up the whole screen? Thanks!

---

### Post by ajgreeny on 2009-09-06
Your friend's computer probably has a lower resolution than your so you may need to change the configuration of grub, though I am not certain exactly what you mean by grub; are you talking of the grub menu, or the splash screen which then appears with the lengthening bar?  If the menu itself, I don't think you can do anything, but for the following splash screen, you can set the resolution to a number of options with the vga= option shown below.

Configure GRUB

Open you GRUB configuration file.  sudo gedit /boot/grub/menu.lst

To proceed, you'll need to know the framebuffer code for your desired resolution:    

Resolution

vga=785        640x480

vga=788        800x600

vga=791        1024x768

vga=794        1280x1024

Automatic (and update-proof) GRUB Configuration

Find the line
# defoptions=quiet splash

and add your framebuffer resolution code, e.g. (for 1024x768)

# defoptions=quiet splash vga=791

Save the file, then execute  sudo update-grub

---

### Post by kyle2595 on 2009-09-08
Hi, sorry for being so vague and sorry for it taking this long for me to respond.  I have attached some pictures of grub so you know what I am talking about.  First off, what is the  framebuffer code and how do I find it?  Second, how do I figure out my desired resolution? I know that my laptop screen is 12 inches wide by 7.5 inches high.  Thank you for putting up with my lack of Ubuntu knowledge.

---

### Post by ajgreeny on 2009-09-08
Sorry, but those codes only affect the splash screen, as far as I'm aware, and do not make any difference to the grub menu, which you show in these pics, but if you want to try the nearest one to your required resolution, you will need to open the grub menu list file with ```
gksudo gedit /boot/grub/menu.lst
```and edit the line as shown in my previous post.  You will need to know the actual screen resolution of your computer to do this, and will find that from the machine's manual.

I hope that helps.

---

