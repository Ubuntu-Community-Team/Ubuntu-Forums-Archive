---
title: "Shell text unreadable"
date: 2010-07-26
forum: General Help
---

### Post by cypherdtraitor on 2010-07-26
I recently used the startup manager to make some aesthetic adjustments to my boot screen. Unfortunately this led to 2 problems that I think may be related.

**THE PROBLEM:**
The first and worst problem is that whenever I enter the terminal by pressing control-alt-function key, the text appears as blotchy colors that are totally unreadable. I cannot upload a screenshot because it is in the terminal. This prevents me from doing maintenance without using the GUI.

The related but unimportant problem is that my ubuntu boot splash is strangely distorted. It is squeezed sideways to about half my screen, and then another boot splash is displayed on the right half of the monitor.

**WHAT I DID**
I modified the start-up manager. I can't remember everything I did, but here are some steps:
*Under display, I changed resolution from unspecified to 1024x768. I cannot change it back to unspecified, and I cannot select a widescreen resolution. I have a 1440x900 widescreen monitor.
*I specified a higher color depth, but lowered it back to 8 bits after I ran into this problem.
*I played with the bootloader colors, but it appears as if I did not select that they would be used. Instead, I have left the "Use colours in the bootloader menu" tick box on the appearence tab unchecked.
*I selected a background image for the grub.

I just found a restore original settings button, and am rebooting. I guess I'll be back.

---

### Post by wojox on 2010-07-26
Try choosing a different Font from the Terminal.

---

### Post by AlphaLexman on 2010-07-26
If your reboot didn't work, I SEEM to remember something about a kernel option vga=somehexcode that makes terminals (like Ctrl-Alt-F1) use more colors, maybe fonts too?

---

### Post by cypherdtraitor on 2010-07-26
The restart worked with little finangling. Which is lucky, because I needed the terminal to re-connect to the internet.

Thanks for the advice guys.

**SOLUTION:**

1.)go to SYSTEM>ADMINISTRATION>STARTUP MANAGER
2.)enter root password to open GUI interface
3.)go to the advanced tab
4.) click "restore original settings"
5.) click close
6.) restart the computer

Note: this will reset your grub background, correct resolution issues on the boot splash, and fix the terminal "blotting" effect.

---

