---
title: "Unity &quot;reset button&quot;?"
date: 2012-09-18
forum: General Help
---

### Post by Ansible on 2012-09-18
My unity experience has degraded since I first installed 12.04. Is there a way I can get back to how it used to be without reinstalling?  Stuff that's not working right:

- on alt-tab, only the current top window shows its contents.  The others are blank, or partially drawn.

- windows key -> alt used to bring up a window of unity shortcuts.  Now it doesn't do anything.

- I'm not 100% sure, but I think that my windows don't look as slick as they used to.  The top bar with the maximize and minimize buttons looks blocky and non-unity-ish.

- shutting down often takes 30 seconds or so, it used to be immediate.  Not necessarily anything to do with the GUI though.  I have postgres installed, maybe that has some cleanup to do before exit.  

I think that the culprit may be nvidia vs intel.  I'm blessed with one of those optimus laptops (thinkpad w520) that has both.  Someone told me that if I changed the bios to dicrete graphics (ie nvidia chipset) and installed the nvidia drivers then multiple monitors would Just Work.  Well for me not so much.  Pretty sure that it was that unfortunate installation and xorg.conf tweaking by the nvidia control panel that hosed things.

At any rate, I have a bunch of software installed and configured, and I'd rather not reinstall everything at this point.  Suggestions?

---

### Post by zero2xiii on 2012-09-18
> **Ansible said:**
> 
I think that the culprit may be nvidia vs intel.  I'm blessed with one of those optimus laptops (thinkpad w520) that has both.  Someone told me that if I changed the bios to dicrete graphics (ie nvidia chipset) and installed the nvidia drivers then multiple monitors would Just Work.  Well for me not so much.  Pretty sure that it was that unfortunate installation and xorg.conf tweaking by the nvidia control panel that hosed things.

At any rate, I have a bunch of software installed and configured, and I'd rather not reinstall everything at this point.  Suggestions?

Hay,

Try booting into safe graphical mode and see how the performance is altered (if at all) as this will give you much more direction and confirm whether or not it is graphics related. If you have established that it is definitely graphics, then you can start debugging that.

Cherz

---

### Post by Ansible on 2012-09-18
I forgot to mention a couple of other symptoms of my current problems:

- laptop doesn't go to sleep anymore when I close the lid.
- when I close the lid and reopen it, the touchpad only does scrolling, it doesn't move the mouse around.  I have to use the 'pointing stick' instead to move the mouse.  

So whatever is going on, it seems to be affecting mouse input.

How this may be relevant is that when I boot into 'recovery mode' from grub (I assume that's what you meant for me to do) and then into low graphics mode, I get a dialog that says "what would you like to do" and that dialog has I believe four options, and 'ok' and 'cancel'.  Unfortunately at that point I don't have a mouse pointer, and the dialog is unresponsive to any keyboard input.  I ended up just rebooting.

---

