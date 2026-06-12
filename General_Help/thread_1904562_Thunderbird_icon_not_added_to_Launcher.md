---
title: "Thunderbird icon not added to Launcher"
date: 2012-01-05
forum: General Help
---

### Post by ddjolley on 2012-01-05
Running Ubuntu 11.10.  When I launch Thunderbird from the Dash the application is launched just fine.  However, no corresponding icon is added to the Launcher.  Any ideas why?  Thanks for any input.

           ... doug

---

### Post by Basher101 on 2012-01-05
meaning when you launch the program, the window appears but no icon on the launcher or that when you close it that the icon disappears? not quite sure what you exactly mean.

---

### Post by ddjolley on 2012-01-05
> meaning when you launch the program, the window appears but no icon on the launcher

Yes,  That is correct.  When I launch Thunderbird the application opens correctly as one would expect.  However, no icon is added to the launcher.

 > or that when you close it that the icon disappears?

No.  I believe that would be normal behavior unless the "Keep in Launcher" option were selected.  The Thunderbird icon never appears in the Launcher.

Thanks.

          ... doug

---

### Post by imachavel on 2012-01-05
try it:

[http://www.cyberciti.biz/faq/install-thunderbird-2-in-linux/](http://www.cyberciti.biz/faq/install-thunderbird-2-in-linux/)

and like it. then tell me what u think

---

### Post by ddjolley on 2012-01-05
Never mind.  The problem seems to have fixed itself.  

I never look a gift fix in the mouth, although (from one perspective) it's always a bit disconcerting when a
problem fixes itself.

Anyway, thanks to all.

            ... doug

---

### Post by pretty_whistle on 2012-01-05
> **ddjolley said:**
> Never mind.  The problem seems to have fixed itself.  

I never look a gift fix in the mouth, although (from one perspective) it's always a bit disconcerting when a
problem fixes itself.

Anyway, thanks to all.

            ... doug
Hope it stays fixed for you.  I have a similar problem where my icon vanishes and a question mark is put in it's place for a while.  I try to fix mine but it won't stay fixed.

---

### Post by Stimpy84 on 2012-01-11
> **ddjolley said:**
> > meaning when you launch the program, the window appears but no icon on the launcher

Yes,  That is correct.  When I launch Thunderbird the application opens correctly as one would expect.  However, no icon is added to the launcher.

 > or that when you close it that the icon disappears?

No.  I believe that would be normal behavior unless the "Keep in Launcher" option were selected.  The Thunderbird icon never appears in the Launcher.

I'm afraid I'm having precisely this problem. I at first thought it might be due to the messaging menu integration (somehow that Thunderbird is running in the background), but even by launching it in safe mode (thunderbird -safe-mode), no icon appears in the Launcher and I can't alt+tab to it as it doesn't appear in the Switcher either.

The Thunderbird window is open however and otherwise functions as expected. I find myself using Super+W (Ubuntu's "Expose") to find Thunderbird when it becomes hidden behind other windows.

What bothers me most is that because the icon never appears in the Launcher, I can't right-click it to "Keep in launcher".

Any suggestions would be most welcome!

---

### Post by Frogs Hair on 2012-01-11
I create / replace my default Firefox Nightly icon because it clashes with my icon sets .The default Thunderbird icon is also in the same location , which is file system usr/shere/pixmaps .

The Thunderbird icon that appears in the Unity launcher is the icon from the set in use and for me is stored in usr/share/icons . There is also the option to place icons in home hidden .icons .

I wonder if something may be inhibiting the path to the icon . If it is a launcher problem the following may help . ```
unity --reset-icons
```

---

### Post by Stimpy84 on 2012-01-11
Running that command restored all the default applications to the launcher, and sure enough, everything's fixed. Thunderbird is now in the list!

I'm thinking that maybe resetting the icons wasn't even necessary: I haven't rebooted for weeks and maybe just restarting Unity resolved the problem.

Thanks for the resolution!

---

