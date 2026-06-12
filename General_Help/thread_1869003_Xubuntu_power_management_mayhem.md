---
title: "Xubuntu power management mayhem"
date: 2011-10-25
forum: General Help
---

### Post by HappyLinux on 2011-10-25
I previously had a problem with Xubuntu freezing up regularly, and I wasn't the only one suffering from it.

[http://ubuntuforums.org/showthread.php?t=1862210]("http://ubuntuforums.org/showthread.php?t=1862210")

However, even though that problem has somehow rectified itself, another problem with power management has cropped up.

I always disable features like hibernate or suspend or whatever they're called for the main system, the HDD etc. I only set it for the monitor and use it like a screensaver sort of thing.

I've gone into the settings and said the monitor to go into standby after 20 minutes of inactivity. However, the problem is that this time doesn't get adhered to by the system.

One example, is that I've got up from the computer to make a cup of coffee which took a matter of a few minutes, came back and my screen has powered down.

Another example is that I've left my computer and went out to take my dog for a walk. That took something like 40 minutes. Came back and the screen hadn't powered down.

Can anyone understand what might be wrong?

---

### Post by gsmanners on 2011-10-25
The problem is that you probably still have two applications trying to control the power: xfce-power-manager and xscreensaver. You need to configure one and disable the other. In my case, I always configure xscreensaver and disable xfce-power-manager, but many other people do the opposite (or just put up with both and the mayhem).

---

### Post by HappyLinux on 2011-10-25
OK, I'll see if that helps?

---

### Post by Parksy on 2011-10-25
I noticed a similar problem today on my laptop, Ubuntu 11.10.  The screen would dim automatically and shutting the lid would put it to sleep...both things I had disabled.  A reboot seems to have fixed it for me.

---

