---
title: "Booting into Live Environment Screen is Extremely Dark"
date: 2011-04-18
forum: General Help
---

### Post by user1397 on 2011-04-18
I have a Gateway NV59C09u laptop, I tried running both maverick and the latest beta of natty as live usb's to no avail.  It boots fine, but at the first screen the light is so dark that I can't really read anything nor see the mouse pointer, I can just barely make out a window-looking thing.  Trying to increase the brightness using my F-keys doesn't do anything.

It's gotta be some kind of graphics related issue, because booting the alternate iso works fine.  If I could figure out a way to boot the ubuntu-desktop live image via a different video driver that would probably work, but I'm not sure how to do that (ctrl+alt+f1 does nothing).

Any ideas?

---

### Post by user1397 on 2011-04-19
bump

---

### Post by Rubi1200 on 2011-04-19
Have you tried using i915.modeset=1?

---

### Post by user1397 on 2011-04-19
> **Rubi1200 said:**
> Have you tried using i915.modeset=1?

Hmm, I'm not exactly sure what you mean by that.  How do I set that?

---

### Post by Rubi1200 on 2011-04-19
When the LiveUSB starts you should have an option to edit the entry, usually by hitting Tab or Esc (something like that). It should then show you the boot line which will probably end with quiet splash.

Add the parameter I mentioned before after quiet splash so it looks like this:

> quiet splash i915.modeset=1

Then, Enter to boot.

---

### Post by user1397 on 2011-04-19
> **Rubi1200 said:**
> When the LiveUSB starts you should have an option to edit the entry, usually by hitting Tab or Esc (something like that). It should then show you the boot line which will probably end with quiet splash.

Add the parameter I mentioned before after quiet splash so it looks like this:



Then, Enter to boot.
unfotunately, that did not work. i'm going to play around with some different parameters and see what happens

---

### Post by user1397 on 2011-04-19
ahah! the acpi=off setting worked!  awesome, thanks for the help Rubi1200 ;)

---

### Post by Rubi1200 on 2011-04-19
No problem, you are more than welcome :-)

Glad you got it sorted out.

For future reference, this link has useful information on setting different parameters:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

