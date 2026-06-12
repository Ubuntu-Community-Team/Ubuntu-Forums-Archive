---
title: "Xorg for xubuntu?"
date: 2010-01-13
forum: General Help
---

### Post by david819 on 2010-01-13
Running Karmic Xubuntu on a Gateway NV7802u.  Made the classic mistake of installing multiple new programs without rebooting to make sure it is possible to still boot.  I installed compiz, compiz-config-something.or.other, emerald, and something that I think was called fusion-plugin.  It's supposed to put an icon on your panel for editing your compiz settings I think.  Anyway, compiz was working beautifully.  Rebooted computer to deal with suspend/audio issue, and I run into the wall.  I get past the Ubuntu splash screen, and it loads the windows I previously had open, but I get no desktop or panels.  Computer sits there with the little circle of circles thinking.  Tried to alt-f2 run the panels, and it brings up the run box, but it is unresponsive, and without the little minimize, maximize, close buttons.  ctrl-alt-f1 my way back to a terminal, run top and it shows Xorg eating 25% of my cpu, but quite clearly accomplishing nothing.  If I understand/remember correctly, Xorg runs all of your startup processes for the desktop.  I wanted to edit the Xorg and maybe remove whichever program is muddying the mix, but evidently there is no xorg.conf.  At least not in the X11 folder.  I googled a bit, and can't find someone mentioning where in Xubuntu 9.10 I can edit the startup processes.  Sooooo, after a long-winded explanation of my travels, what is the Xorg equivalent, or perhaps new folder location, for xorg.conf for Xubuntu?

---

### Post by falconindy on 2010-01-13
> **david819 said:**
> what is the Xorg equivalent, or perhaps new folder location, for xorg.conf for Xubuntu?
Close, but Xorg **is** desktop. It's also not what's directly causing your problem. Pre Compiz you were fine, right? Post Compiz, well... here you are. It's most likely an issue with compositing.

Looks like you're running Intel graphics. Check out [KMS]("https://wiki.ubuntu.com/X/KernelModeSetting"), and see if enabling it helps.

---

### Post by Leppie on 2010-01-13
the version of xorg in karmic doesn't require the xorg.conf anymore to run. if you cannot find it, it's never been customized.

---

### Post by david819 on 2010-01-13
Thanks for the responses, I would like to try the KMS route later this evening, but is there a temporary way for me to prevent compiz from loading on boot, so that I can at least have my desktop back?  Keeping in mind that whatever I do, must be done from a terminal.

---

### Post by Leppie on 2010-01-13
you could try to remove the packages you installed before this happened:
```
sudo apt-get remove compiz compiz-fusion-* compizconfig-*
```

---

### Post by david819 on 2010-01-13
ok, got myself back in by removing everything from my /home/<username>/.cache/sessions folder.  Rebooted, and I am good to go.  Honestly, I'm not really sure why this worked.  I understand that it got rid of any saved sessions, and I am assuming that means preventing compiz, etc., from reloading on boot.  I never set it to run on boot, so it must have been doing so simply because it was running when I shutdown.  Am I correct in this assumption?  Well, my compiz issue isn't solved, but it isn't a discussion for general help.  So thanks to all, I'm going to end this one.

---

