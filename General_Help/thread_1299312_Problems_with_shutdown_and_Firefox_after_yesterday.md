---
title: "Problems with shutdown and Firefox after yesterdays upgrade"
date: 2009-10-23
forum: General Help
---

### Post by doftya on 2009-10-23
After yesterdays upgrade, I've had a couple of issues crop up.
 
First of all, when I try to shut down Ubuntu, the panels disappear then the screen freezes on the rest of the destop. I can move the pointer around and select desktop items, but can't open them. It freezes right there and will not shutdown further unless I press the on/off button on the CPU.
 
Secondly, there are problems with Firefox. My bookmarks have disappeared, and I can't load a backup. I also cannot add new bookmarks. The browser history is frozen on Tuesday's activity. In fact, if I browse around a few websites, nothing is saved to the history at all, ie. the back button will not become active.
 
Any ideas?

---

### Post by Khalicl13 on 2009-10-23
I'm on the same boat as you since yesterday's upgrade.  I can click on links or open websites from shortcuts on the desktop but I can't go anywhere from the address bar or the search bar.  I can't even log into GMail.  I tried using Opera but for some reason Opera wouldn't even launch.  I'm not certain yet if that's a separate issue but I don't recall have that issue before this latest upgrade.

I haven't seen any solutions yet but in the meantime, is there a way to undo the upgrade and go back to the previous state?

---

### Post by doftya on 2009-10-23
Oh, yeah, you reminded me of that. The enter key does not work, and clicking on an "enter" button does not work either.  I can't type in addresses, or use the search bar either.
 
I havn't been able to undo the update yet.
 
Anyone have any ideas?

---

### Post by Khalicl13 on 2009-10-23
WHOOOHOO!! I managed to get it working by reverting back to the previous linux kernel by running the following in the terminal:

sudo dpkg -i /var/cache/apt/archives/kernel-package_11.001_all.deb 

I got the idea from this thread: [http://ubuntuforums.org/showthread.php?t=464479](http://ubuntuforums.org/showthread.php?t=464479)

I don't know if this is the best fix but it's resolving the immediate issue of being able to Firefox and Opera again.  Something is screwy with the latest linux-kernel upgrade.

---

