---
title: "help please, can't boot up."
date: 2011-06-03
forum: General Help
---

### Post by farno_78 on 2011-06-03
Hi guys, 

I have been using ubuntu for a few years now for basic everyday use and have always found this forum very helpful, have never needed  to post previously as I have alsways found the fix I'm after.

Unfortunately I'm struggling on this one and am in a bit of a panic as my machine will no longer boot up, basically I plugged in a second screen which was not displaying properly (kinda fuzzy), I knew the screen was OK so looked for a fix.  This is what I came across.

[http://ubuntuforums.org/archive/index.php/t-1467220.html](http://ubuntuforums.org/archive/index.php/t-1467220.html)

So I added text "nomodeset", saved and restarted, now all I get is a very brief start up logo which is distorted followed by a black screen, nothing else happens.

Is it possible for me to get into the terminal to reverse what I did without booting into the main os, by using a live disk?  

I am using 10.04 if that helps.  Any help would be greatly appreciated.

Nathan

---

### Post by farno_78 on 2011-06-03
Right, I'm booted into recovery mode using the shift key when booting up and have "fixed broken packages" and then "resumed".  I am now in what looks like the terminal (after typing my user and password) but taking up the whole page.  Should I try reversing what I did above now?  Will it open gedit for me to amend and save etc?

---

### Post by drs305 on 2011-06-03
You should be able to restore your normal boot temporarily from the Grub2 menu. At the Grub menu, highlight the desired menu item and press 'e' to edit it. Cursor to the end of the 'linux' line and remove the 'nodmodeset' option you previously added. Press CTRL-x to boot.

If it boots to the desktop, open the /etc/default/grub as root and remove the nomodeset entry from the "GRUB_CMDLINE_LINUX_DEFAULT=" line (or wherever you added it).
```
gksu gedit /etc/default/grub
```

Save the file, then run "sudo update-grub". This should restore the boot to the condition before you added 'nomodeset' (but will not undo any changes you made to your video settings after doing so).

---

### Post by farno_78 on 2011-06-03
Brilliant :P I picked the low graphics mode after holding the shift key and then deleted the text I added earlier.  It's lucky I had an old laptop I could use to get here!

Thanks for your help, I can stop panicking now!

---

### Post by drs305 on 2011-06-03
Edit: Looks like you just did it. Thanks.

Glad it's working again. If you are finished with this thread, please mark it SOLVED via the 'Thread Tools' link at the top right of the first post. It helps both those looking for solutions as well as those monitoring the thread. (And it's reversible!).

Happy Ubuntu-ing !

---

### Post by farno_78 on 2011-06-03
Yup just did it, took me a while to work it out.  I think I'll be posting again soon about a fuzzy 2nd screen!  Thanks again.

---

