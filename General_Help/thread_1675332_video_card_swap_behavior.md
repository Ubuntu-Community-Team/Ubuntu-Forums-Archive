---
title: "video card swap behavior"
date: 2011-01-25
forum: General Help
---

### Post by wog on 2011-01-25
Quick question: If I take out the existing video card and put in another one of a different type (but not a different brand), how does Ubuntu behave?

I know what Windows typically does. Windows starts up the screen using a default video driver which is at least 1024 by 768 and then asks you what this new bit of hardware is and asks where the drivers are.

I'm pretty sure Ubuntu has default drivers of its own, but I don't know what their resolution is. If anyone knows, that would also be helpful.

Thanks in advance!

---

### Post by DanneStrat on 2011-01-25
I had a look around and found this:

[http://ubuntuforums.org/showthread.php?t=1115660](http://ubuntuforums.org/showthread.php?t=1115660)

This thread is a bit older, but you might want to check it out:

[http://ubuntuforums.org/showthread.php?t=234231](http://ubuntuforums.org/showthread.php?t=234231)

I wouldn't rely upon the second one because the way

xorg works has changed in later distributions.

---

### Post by wog on 2011-01-29
I guess I didn't need to worry. 

I swapped the cards, started up the machine and the screen came up fine and in high detail. Checking the video driver, I found the nVidia X Server Settings had identified the new card and put the proper driver in place, so there was no need to go into CLI and apt-get anything.

All done! Thanks for the hand-holding!

---

### Post by DanneStrat on 2011-01-29
> **wog said:**
> I guess I didn't need to worry. 

I swapped the cards, started up the machine and the screen came up fine and in high detail. Checking the video driver, I found the nVidia X Server Settings had identified the new card and put the proper driver in place, so there was no need to go into CLI and apt-get anything.

All done! Thanks for the hand-holding!

You're welcome!

Glad you got it working.

---

