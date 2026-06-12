---
title: "New natty install, graphics glitches"
date: 2011-08-06
forum: General Help
---

### Post by tsantsa31 on 2011-08-06
It has been a long time since I played with a linux flavor.  After messing with osx86 for awhile, I decided to come back to ubuntu.  I installed from a USB stick. The install process went flawlessly, with no apparent graphical glitches.  Once the computer booted up after the initial reboot the graphics are very glitchy. I can't see any much of anything other than the cursor. The edges are striped black and white and I am getting a screen-door effect over the entire desktop.  At the login screen everything is fine...I don't know of keyboard shortcuts to try to change resolutions or any of that other stuff (like I said, it's been QUITE some time since I have played with linux.)

EDIT #2:  Ok, so upon further reading I think it is the Unity thing causing disruption...but not sure...checking checking, one moment please.

Should I try to reinstall or is this a simple fix?

BTW, it was installed on a Dell Dimension 9150 with an ATI gfx card.

EDIT:  Ok, I was able to notice (re: i am stupid) that I can change the type of ubuntu to login with. I am currently in ubuntu classic and desktop looks fine. I am updating all the software and downloading Compiz configuration tool.  I am hoping that solves the problem.

---

### Post by tsantsa31 on 2011-08-06
I'm replying just to bump. I know it's frowned upon.

I fixed the problem. Honestly I don't know what I did other than try to install fglrx then found that it doesn't work with my card (ati x1050) and uninstalled it. Next time I tried to reboot into full ubuntu with unity, it worked...

(EDIT: one thing i did do, now that i remember, is I installed unity 2d option.  I booted into unity 2d once then booted into full ubuntu unity after that.  I don't know if it's still 2d but the icons changed slightly after that.

---

### Post by Basher101 on 2011-08-06
Try to edit the kernel line before booting. Simply press "e" when you are over Ubuntu in the grub menu (instead of enter) and add to the line: ```
quiet splash **_nomodeset_**
```
after that press ctrl+x to boot (do not exit the "editing" interface)

---

### Post by tsantsa31 on 2011-08-07
> **Basher101 said:**
> Try to edit the kernel line before booting. Simply press "e" when you are over Ubuntu in the grub menu (instead of enter) and add to the line: ```
quiet splash **_nomodeset_**
```
after that press ctrl+x to boot (do not exit the "editing" interface)


What does this do exactly?

---

### Post by tsantsa31 on 2011-08-07
The next day, after the computer was off all night, the graphics got all glitchy again. It's an ATI x1050 card. I wonder if a cheap nVidia card would do better.

---

### Post by wildmanne39 on 2011-08-07
Hi, nomodeset is just for a one time boot so you can fix your driver issue, unless you made it persistent, which you can do with this link, but I would only do that as a last resort.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

