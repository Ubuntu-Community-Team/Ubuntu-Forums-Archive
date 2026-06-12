---
title: "Need help! How to delete files using live-cd because..."
date: 2010-09-24
forum: General Help
---

### Post by dollarside on 2010-09-24
Hey!

Background: My gnome-do is acting up on my Ubuntu 10.04.1 LTS (Lucid Lynx)and I cannot type nor click (although I can move my mouse). I therefore need to delete gnome-do so that it will not start up when I boot. People say I can do so by going into recovery mode option, but my resolution is messed up and I cannot see the options (at all).

May I ask how to:

1)Change the boot screen resolution with a live cd or something?
2)I cannot delete my files on Ubuntu using the live-cd, is there any way that I can?

I really need help with this. Thank you!

---

### Post by mikewhatever on 2010-09-24
The recovery mode is usually shown in the boot menu, long before Ubuntu is loaded. Alternatively, hit Ctrl+Alt+f1 at the login screen instead of logging in, login at the black screen prompt and remove whatever you need to. When done, type **sudo reboot** to reboot, or **exit** to logout. Ctrl+Alt+f7 should bring you back into GUI.

---

### Post by dollarside on 2010-09-24
> **mikewhatever said:**
> The recovery mode is usually shown in the boot menu, long before Ubuntu is loaded. Alternatively, hit Ctrl+Alt+f1 at the login screen instead of logging in, login at the black screen prompt and remove whatever you need to. When done, type **sudo reboot** to reboot, or **exit** to logout. Ctrl+Alt+f7 should bring you back into GUI.

Thanks for replying!

I'm a little confused here. Normally, there will be a grub bootloader stage before I choose to boot into Windows XP or Ubuntu (and the other recovery modes). If I choose Ubuntu (as usual), then I''ll leave it untouched, and I'll be automatically logged in etc etc. So now I go down to ubuntu recovery mode (I do not remember the exact title for this option), I press enter and wait. A few options will appear, but I cannot read the words because they are pixelated and just plain illegible. What do I do? 

Is the recovery mode a gui? Or do I need to use command lines?

---

### Post by SlugSlug on 2010-09-24
boot up normally,

once your in hit ctrl+alt+F1

this will give you terminal access  login with user/pass
-- so to reinstall gnome-do

sudo aptitude reinstall gnome-do

---

### Post by mikewhatever on 2010-09-24
The recovery mode is CLI only, which is good, since you have resolution problems when in GUI.

---

### Post by dollarside on 2010-09-25
Solved! Thanks for all your inputs guys, this is how I fixed it:

I booted up into Ubuntu as usual, and before it loads desktop, I pressed Ctrl+Alt+F1, then I got to this text console(that's what it's called?). I first typed my username, then my password, then I typed in:

sudo apt-get remove gnome-do

then it did it's work, and I typed in "y" then press enter as it asks for confirmation. Then rebooted and voila!

Happy now I am. Thanks again!

---

