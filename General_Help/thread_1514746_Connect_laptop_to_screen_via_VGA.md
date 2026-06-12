---
title: "Connect laptop to screen via VGA"
date: 2010-06-21
forum: General Help
---

### Post by mosquetero on 2010-06-21
Hi!

I am trying to connect my laptop to my new screen but the screen gets no signal. I use a NVIDIA card with the latest version available. Can anyone help me please?

Thanks in advanced

---

### Post by gkumar on 2010-06-21
First of all, we need to know if you have the nvidia drivers installed or not. If you do, under System > Administration, there should be an entry for the "Nvidia X Server Settings." You'll want to go to that to set up your displays. In the window that opens up, you'll want to go to "X Server Display Configuration" in the sidebar on the left. Then, you'll see a graphical representation of your display setup. If you don't see your external screen, connect it, and click the "Detect Displays" button, and it should hopefully show up. In order to set it up correctly, you'll want to click the configure button, and select either Twinview to extend your desktop, or clone to duplicate it.

If that application doesn't exist in your menu, you either don't have, or don't need the drivers installed. You'll then want to go to System > Preferences > Monitors, and configure your external display from there.

Good luck, and let me know if there are any issues.

EDIT: I just realized that you mentioned that you have the latest version of the drivers installed, so the first paragraph is the only one that applies to your setup.

---

### Post by mosquetero on 2010-06-21
Thank you so much!!

It is working :D

---

