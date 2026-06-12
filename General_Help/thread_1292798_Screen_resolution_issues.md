---
title: "Screen resolution issues"
date: 2009-10-16
forum: General Help
---

### Post by nmgarnett on 2009-10-16
I've just installed Ubuntu 9.10 Beta and have the following problem; the screen resolution pre-login and post log-in is about 1900 x 1400 rendering the login screen with Ubuntu login and password boxes in the bottom right hand corner of my 1200 x 800 laptop. Post login I have adjusted resolution accordingly and all is fine, this has no effect on pre and post login resolution.
I am a newbie so some gentle direction would be very helpful...
Nick Garnett

---

### Post by ajgreeny on 2009-10-16
I think you need to change the resolution of grub and subsequent screens until the login box of gdm appears and you should be able to do that with the following.

Open you GRUB configuration file.  sudo gedit /boot/grub/menu.lst

To proceed, you'll need to know the framebuffer code for your desired resolution:    
vga=785        640x480
vga=788        800x600
vga=791        1024x768
vga=794        1280x1024
vga=870        1280x800

Find the line
# defoptions=quiet splash

and add your framebuffer resolution code, e.g. (for 1024x768)

# defoptions=quiet splash vga=791

Save the file, then execute  sudo update-grub

I don't know what the figure is for exactly your resolution, but I suspect one or other of those will help.  You may also be able to change the resolution of usplash in /etc/usplash.conf by putting your own figures in.

Here's mine:
```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1280
yres=1024
```
I see you are running 9.10 so I don't know how things will have changed for grub2, but if you are still running legacy grub, the above may help.

---

### Post by nmgarnett on 2009-10-17
Thanks for the answer and yes it is Grub 2. Since I posted I've updated and the problem still exists + allUSB ports have stoped working?
Nick Garnett

---

