---
title: "Fix Firefox profile without losing my settings?"
date: 2009-08-13
forum: General Help
---

### Post by MountainX on 2009-08-13
I am running Jaunty. I recently installed Firefox 3.5 (Shiretoko) from the Ubuntu repositories. The installation process copied my profile from Firefox 3.0 automatically.

I'm having some [issues]("http://ubuntuforums.org/showthread.php?t=1238437") that I think are related to problems with the profile. Is there a way to fix a profile without losing my info?

If not, I can delete this profile and recreate it? I have my original Firefox 3.0 profile still. How do I perform a manual "migration" to 3.5 using my 3.0 profile data?

---

### Post by aysiu on 2009-08-13
If you paste the command ```
firefox -safe-mode
``` into [url=http://www.psychocats.net/ubuntu/terminal]the terminal[/code] you will have the option to disable certain parts of your profile selectively.

---

### Post by Rob_H on 2009-08-13
How is it broken? You can certainly start a new profile and selectively copy out bits from the old profile like bookmarks and such. Just move the contents of **~/.mozilla/firefox** and **~/.mozilla/firefox-3.5** to a different location for backup. Firefox should create a new profile the next time you launch it.

Then, to selectively move settings from your old profile to your new one, see [this article]("http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox") on MozillaZine.

---

### Post by MountainX on 2009-08-13
It turns out that [my problem]("http://ubuntuforums.org/showthread.php?t=1238437") is not related to the Firefox profile. I tested with a newly created profile (no modifications from default values) and [the problem is still there]("http://ubuntuforums.org/showthread.php?t=1238437").

But at least I learned a few things about profiles. Thanks. Now I need to solve [my original problem]("http://ubuntuforums.org/showthread.php?t=1238437").

---

### Post by lovinglinux on 2009-08-14
> **MountainX said:**
> It turns out that [my problem]("http://ubuntuforums.org/showthread.php?t=1238437") is not related to the Firefox profile. I tested with a newly created profile (no modifications from default values) and [the problem is still there]("http://ubuntuforums.org/showthread.php?t=1238437").

But at least I learned a few things about profiles. Thanks. Now I need to solve [my original problem]("http://ubuntuforums.org/showthread.php?t=1238437").

Just to let you know, if you delete ~/.mozilla/firefox-3.5, Shiretoko will copy your profiles from FF 3.0 again. It does that every time it can't find an usable profile.

About your original problem, I don't know what could be causing it, but I recommend using [Download Statusbar](https://addons.mozilla.org/en-US/firefox/addon/26) extension. It might solve your problem, since it allows to open the folder and the file downloaded from a context menu. It also allows to open the file by double-clicking the downloaded file.

---

### Post by MountainX on 2009-08-14
> **lovinglinux said:**
> Just to let you know, if you delete ~/.mozilla/firefox-3.5, Shiretoko will copy your profiles from FF 3.0 again. It does that every time it can't find an usable profile.


Thanks. That's good to know. 

... or it would have been good to know if I had kept Shiretoko. I quickly learned to hate Shiretoko. I found SwiftWeasel and I love it. It is faster and everything works. Problem solved.

---

### Post by lovinglinux on 2009-08-14
> **MountainX said:**
> Thanks. That's good to know. 

... or it would have been good to know if I had kept Shiretoko. I quickly learned to hate Shiretoko. I found SwiftWeasel and I love it. It is faster and everything works. Problem solved.

Swiftweasel is faster because it's compiled with optimizations for your processor family and with Profile-Guided Optimization, but it uses the same code as Shiretoko and Firefox.

I use Swiftweasel on a notebook with amd processor, but I compile Firefox myself with the same optimizations on my desktop pc with Intel Prescott.

---

### Post by MountainX on 2009-08-14
> **lovinglinux said:**
> it uses the same code as Shiretoko and Firefox.

Yes, but apparently some defaults or other settings are different, which led to my troubles with Shiretoko. Anyway, it was good because the problems led me to finding Swiftweasel, which, as you point out, is optimized for my cpu. It may not be as fast as FF under Wine, but its good enough for now.

---

