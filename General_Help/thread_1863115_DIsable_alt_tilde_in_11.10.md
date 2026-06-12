---
title: "DIsable alt tilde in 11.10"
date: 2011-10-17
forum: General Help
---

### Post by akudlick on 2011-10-17
Hi,

I just upgraded to 11.10, and alt tilde is now a system hot key.  I use this (a lot) for IntelliJ; I want to disable it.  I checked Keyboard > Shortcuts, but it is not there to disable.

Is there a way I can do this?

---

### Post by GooglieS on 2011-10-21
Any updates? I dont fount any binding in ccsm for this :(

---

### Post by akudlick on 2011-10-21
Nope, no good news :(  This posting was my only hope....

---

### Post by Tweak42 on 2011-12-09
> **akudlick said:**
> Hi,

I just upgraded to 11.10, and alt tilde is now a system hot key.  I use this (a lot) for IntelliJ; I want to disable it.  I checked Keyboard > Shortcuts, but it is not there to disable.

Is there a way I can do this?

Stumbled here looking for the same answer.  Unfortunately I discovered that it's apparently hard coded.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/878915?comments=all](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/878915?comments=all)

---

### Post by akudlick on 2011-12-09
Boo! I guess they figured no other applications use this key.  Thanks for the info though.

---

### Post by tomekn on 2012-01-15
I am yet another IntelliJ IDEA user. Is it still not possible to disable or change this shortcut?

---

### Post by cbmanica on 2012-02-17
Greetings, fellow furious IntelliJ IDEA users.  I can report that it IS possible to fix this idiocy in Ubuntu 11.10, despite what that bug report says: 

1) Install the compizconfig-settings-manager package
2) The setting we are all searching for is Desktop -> Ubuntu Unity Plugin -> Switcher
3) Change "Key to flip through windows in the switcher" to something else

Now, whoever buried this setting here and called it something so bizarre as to make Googling for it the exercise of pain I have just undertaken should be killed, but hey, that's what we get for running Linux.  HTH!

P.S. For anyone who might be tempted to follow the advice here, [http://ubuntuforums.org/showthread.php?t=1859392](http://ubuntuforums.org/showthread.php?t=1859392), DON'T DO IT, as not only does it NOT work, the custom keybindings feature is itself horribly non-documented and also just flat broken.

---

### Post by akudlick on 2012-02-17
Thanks!  This worked perfectly! Now I can go back to my old, productive self.

---

### Post by dal on 2012-02-27
> **cbmanica said:**
> Greetings, fellow furious IntelliJ IDEA users.  I can report that it IS possible to fix this idiocy in Ubuntu 11.10, despite what that bug report says: 

1) Install the compizconfig-settings-manager package
2) The setting we are all searching for is Desktop -> Ubuntu Unity Plugin -> Switcher
3) Change "Key to flip through windows in the switcher" to something else



This works for me - kind of. When I go to that particular window, I see the 'Key to flip through windows in the switcher' shortcut listed as disabled. What I find is that if I set it to a key combination (any key combo) then make it disabled again, it frees up my alt-tilde key combination......until the next reboot. No idea why this change isn't permanent or how to make it so (or why it claims the shortcut is disabled to start with when it isn't) :(

---

### Post by loopum on 2012-05-26
> **cbmanica said:**
> Greetings, fellow furious IntelliJ IDEA users.  I can report that it IS possible to fix this idiocy in Ubuntu 11.10, despite what that bug report says: 

1) Install the compizconfig-settings-manager package
2) The setting we are all searching for is Desktop -> Ubuntu Unity Plugin -> Switcher
3) Change "Key to flip through windows in the switcher" to something else

Now, whoever buried this setting here and called it something so bizarre as to make Googling for it the exercise of pain I have just undertaken should be killed, but hey, that's what we get for running Linux.  HTH!

P.S. For anyone who might be tempted to follow the advice here, [http://ubuntuforums.org/showthread.php?t=1859392](http://ubuntuforums.org/showthread.php?t=1859392), DON'T DO IT, as not only does it NOT work, the custom keybindings feature is itself horribly non-documented and also just flat broken.

This works for me!
Thank you so much.

---

### Post by Duncan J Murray on 2013-05-23
Awesome, thanks so much.  I haven't tried this yet, but this is 1 less barrier for me to upgrade from 10.04!  Maybe I'll go 12.04-Mate anyway, but just in case I go for the G3 classic.

D

---

### Post by oldos2er on 2013-05-23
Old thread closed.

---

