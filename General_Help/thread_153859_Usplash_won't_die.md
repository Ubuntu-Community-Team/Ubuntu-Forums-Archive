---
title: "Usplash won't die"
date: 2006-04-01
forum: General Help
---

### Post by Ian Maxwell on 2006-04-01
I kind of like the old text-only bootup sequence. As such, I turned off and removed usplash from the system. However, the splash screen is still appearing during bootup for a short while, after which the screen returns to text for the rest of the sequence until X starts. What would cause this?

---

### Post by xXx 0wn3d xXx on 2006-04-01
[QUOTE=Ian Maxwell]I kind of like the old text-only bootup sequence. As such, I turned off and removed usplash from the system. However, the splash screen is still appearing during bootup for a short while, after which the screen returns to text for the rest of the sequence until X starts. What would cause this?[/QUOTE]
I think that you need to remove it from your grub menu.lst

> 59. usplash - Well, if you really want to see the nice boot up screen, leave it as it is. I just turned it off anyway. If you want to turn it off, you also need to edit /boot/grub/menu. lst file to comment out the splashimage line and get rid of the splash kernel boot option. -from the speed up the boot process thread.

---

### Post by Ian Maxwell on 2006-04-01
That did it, thank you.

---

