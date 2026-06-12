---
title: "starting GUI"
date: 2006-04-02
forum: General Help
---

### Post by nirav82 on 2006-04-02
I recently installed Ubuntu and after the installation completed linux booted to the command prompt. after logining in i tried startin the GUI using the startx command but it didnt work...got a error saying "command not found" so how can i boot linux into the GUI mode? Thank you.

Nirav

---

### Post by tseliot on 2006-04-02
Turn on your computer and select "Recovery Mode" in the GRUB menu.

It will boot in the command line.

Log in
Then type this:
nano /etc/X11/xorg.conf

Scroll down the file with your keyboard arrows and look for the Section "Device" 

Replace the word in inverted comas beside the word Driver (the word in red in the example) with "vesa"
example:

```
Section "Device"
    Identifier      "Device[0]"
    Driver		"[COLOR="Red"]nvidia[/COLOR]"
```
    

CTRL+O to save
CTRL+X to exit

Then restart your computer by typing:
```
reboot
```

On your next boot you should be able to see the Graphical interface.

---

