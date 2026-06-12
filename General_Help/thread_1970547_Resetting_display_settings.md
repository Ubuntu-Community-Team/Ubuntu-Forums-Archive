---
title: "Resetting display settings"
date: 2012-05-01
forum: General Help
---

### Post by lykwydchykyn on 2012-05-01
My son was trying to fix the display settings on his account, and somehow set it to a resolution that freaks out the onboard video card.  I need to reset his display settings somehow, but I can't find where those are stored.

Other accounts login fine, but logging in his accout crashes the video driver.

I've grepped through his .gconf folder, but I can't find the settings.  Any help?

---

### Post by tomatoe on 2012-05-01
This always restored everything for me

 ```
sudo apt-get purge xserver-xorg xserver-xorg-video-all
 sudo apt-get install xserver-xorg xserver-xorg-video-all
```

and reboot.

---

### Post by lykwydchykyn on 2012-05-01
That's a tad extreme... these were per-user settings anyway.

I managed to find it.  I had to remove his ~/.config/monitor.xml file.  Next time he logged in, default settings.

Thanks for responding, though!

---

### Post by pbrane on 2012-05-01
Sometimes doing this will help.
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by lykwydchykyn on 2012-05-01
Thanks; keep in mind, this was an account-specific problem.  Globally speaking, xorg was fine.  Just his account was messed.

But, like I said, it's fixed now by deleting ~/.config/monitors.xml to reset his personal display settings.

Marking thread solved.  Thanks for all responses.

---

