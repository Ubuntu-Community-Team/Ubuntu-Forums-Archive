---
title: "auto updated and now laptop boots to &quot;_&quot;"
date: 2006-05-08
forum: General Help
---

### Post by oxygen_77 on 2006-05-08
I just updated my laptop using the auto updater that appears in the toolbar in Gnome.  The update included a new Kernel and I think some new XWindows components.  Now when I boot, my machine goes through the normal boot process, after the window that shows the devices that have properly "come up" the screen changes to an underscore.  (I think this is where X should be starting).  Does anyone have any suggestions on how I can gather more information about why this is happening?  As of now, once the "_" appears I cannot do anything.  Thanks!

---

### Post by oxygen_77 on 2006-05-08
Can someone just suggest a good way to boot into some sort of debug mode?

---

### Post by jhorner on 2006-05-08
[QUOTE=oxygen_77]Can someone just suggest a good way to boot into some sort of debug mode?[/QUOTE]

tried booting from the livecd?

or Ctrl + F2-6 and try "startx" in terminal.?

---

### Post by oxygen_77 on 2006-05-10
[QUOTE=jhorner]tried booting from the livecd?

or Ctrl + F2-6 and try "startx" in terminal.?[/QUOTE]No, I didn't; but only because I didn't have one available at the time.  I did however find a way to fix the problem.  I was able to boot into a "safe mode" via GRUB and then from there reconfigure Xwindows (running *xconf* and manually editing the xorg.conf).  I think the ATI graphics card driver that installs with "easy ubuntu" wasn't playing nicely with either my upgraded Kernel or the new Xwindows components.  Once I went back to the generic driver everything started working again.

---

