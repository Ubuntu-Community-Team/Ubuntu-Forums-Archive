---
title: "Bootsplash resolution changed"
date: 2010-05-02
forum: General Help
---

### Post by Hwæt on 2010-05-02
Hi, I recently installed Ubuntu 10.04, and after I rebooted to finish installing my Nvidia drivers, the bootsplash reset itself to a resolution of 800x600. Is there any way to change it back to 1680x1050?

---

### Post by The Thunder Chimp on 2010-05-02
I know there's a package that let's you change your bootloader features (including the resolution) but I just can't put the name on it. I'm sure it's three words written in one, something like managebootloader, but I don't think it's that.

Maybe someone can help me put the word on the package?

---

### Post by The Thunder Chimp on 2010-05-02
startupmanager

---

### Post by WorMzy on 2010-05-02
Check solution #4 in this post: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by Hwæt on 2010-05-04
> **The Thunder Chimp said:**
> startupmanager

That worked perfectly, thank you!

For those wondering what I did:

I installed Startup Manager, changed GRUB's screen resolution to 1600x1024 (my own screen is 1680x1050), and changed the resolution for the boot splash to 1600x1024, as well. Then I checked the "Show boot splash" area, saved my changes, rebooted, and viola!

> **WorMzy said:**
> Check solution #4 in this post: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

That didn't work for me. :(

Thanks for the help, though.

---

