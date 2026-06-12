---
title: "Re: Keyboard Volume dial doesn't change volume"
date: 2012-08-06
forum: General Help
---

### Post by cactux on 2012-08-06
Hello,

This Dell SK-8135 keyboard works fine with Gnome, including the mute button and the "wheel" to lower or increase volume.
However, it does not work with KDE: a kind of popup showing the sound level is displayed, with the cursor moving according to the "wheel" movement, but the sound is not changed.

Do you know how to make this keyboard work in KDE the same way in works in Gnome?

A photo of this keyboard is available in this post:
[http://ubuntuforums.org/showthread.php?t=1443979](http://ubuntuforums.org/showthread.php?t=1443979)

I have KDE and Gnome on the same PC, I just log off and log in again with a different desktop env, same user. Version 12.04

Thanks ;-)

---

### Post by wildmanne39 on 2012-08-06
Moved to own thread!

---

### Post by llamabr on 2012-08-06
From:
[http://wiki.debian.org/Keyboard/MultimediaKeys](http://wiki.debian.org/Keyboard/MultimediaKeys)

Open K > Multimedia > Kmix sound mixer
    Show Mixer Window

    Go to Setting > Configure Global Shortcuts...  



This works fine with Amarok too.

Input Action

This method is more generic.

    Go to 

K > Configuration > Regional & Accessibility > Input Action

    Create new group called "Multimedia"
    Create new action

---

