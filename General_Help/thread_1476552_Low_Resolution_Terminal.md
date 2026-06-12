---
title: "Low Resolution Terminal"
date: 2010-05-07
forum: General Help
---

### Post by Finalfantasykid on 2010-05-07
When I go CTL + ALT + F1 (or F2/F3...) the terminal screen used to be a decent resolution probably 800x600, or something like that, but now it is horribly low resolution, probably 640x480, or maybe even lower, whatever it is, it needs to wrap practically everything I type.  Just showing the default working directory covers over half of the screen.

It didn't used to do this when I first upgraded to Lucid, but now after an update, it is showing in this low resolution.  Second of all, the plymouth loading screen is now also that same low resolution, it used to be the same resolution as the terminal screen when I first upgraded, but now it is just super low.

I am using the NVIDIA driver 195.36.24

---

### Post by ubunterooster on 2010-05-07
in terminal click"edit">profile preferences.


Change the default size

---

### Post by Finalfantasykid on 2010-05-07
Thats not the terminal that I am refering to.  I'm talking about the one when you go CTL + ALT + F1

---

### Post by WorMzy on 2010-05-08
They're called ttys, just incase you were wondering. :)

Try running 'sudo dpkg-reconfigure console-setup'

---

### Post by Finalfantasykid on 2010-05-08
> They're called ttys, just incase you were wondering. :)
Thanks :)

> Try running 'sudo dpkg-reconfigure console-setup' 	

Tried that, but it didn't work.  It seems that is just for modifying the fonts and keyboard settings for the console.

---

### Post by WorMzy on 2010-05-08
Using a smaller font size doesn't help? Or are you already using 8 (which I think is the smallest)?

You might have to add a vga= argument to your grub's kernel line. If you're using grub-legacy, I can help you do that, but if you're using grub2, I'm unsure how you'd set it.

---

### Post by Finalfantasykid on 2010-05-08
Ya after some more searching, I was able to fix the problem by using startupmanager.

---

