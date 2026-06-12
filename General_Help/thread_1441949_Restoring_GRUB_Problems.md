---
title: "Restoring GRUB Problems"
date: 2010-03-29
forum: General Help
---

### Post by Keith1212 on 2010-03-29
I'm following [this guide here]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5") so i can dual boot linux and xp even though it is for an older version of ubuntu. I copied my entire boot folder and this is what it looks like.
[[IMG]http://i212.photobucket.com/albums/cc318/pr0j3ctxb0x/th_Screenshot.png[/IMG]]("http://s212.photobucket.com/albums/cc318/pr0j3ctxb0x/?action=view&current=Screenshot.png")
[[IMG]http://i212.photobucket.com/albums/cc318/pr0j3ctxb0x/th_Screenshot-1.png[/IMG]]("http://s212.photobucket.com/albums/cc318/pr0j3ctxb0x/?action=view&current=Screenshot-1.png")
[[IMG]http://i212.photobucket.com/albums/cc318/pr0j3ctxb0x/th_Screenshot-2.png[/IMG]]("http://s212.photobucket.com/albums/cc318/pr0j3ctxb0x/?action=view&current=Screenshot-2.png")
 Anyways, I got xp installed fine now i'm just wanting to restore my grub so i can choose what to boot. I didn't have a ```
[COLOR=#ff0000]**/boot/grub/menu.lst**[/COLOR]
```[COLOR=#ff0000]** and the **[/COLOR]```
sudo grub
``` says command not found while booting from the Ubuntu 9.10 live cd.

I'm not sure what to do at this point. Thanks for any help.

Edit: Well I figured out how to reinstall the grub and it let me enter it via the grub command. I am now stuck at this point in the picture.
[[IMG]http://i212.photobucket.com/albums/cc318/pr0j3ctxb0x/th_Screenshot-3.png[/IMG]](http://s212.photobucket.com/albums/cc318/pr0j3ctxb0x/?action=view&current=Screenshot-3.png)

---

### Post by oldfred on 2010-03-29
Those instructions are fine for the older versions. Since you installed Karmic as a new install you now have grub2 and the method to reinstall has changed. I hope you did not install grub legacy on top of grub2 as that makes it more difficult to recover.

Follow the version for grub2 with Karmic 9.10 or later.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Keith1212 on 2010-03-30
> **oldfred said:**
> Those instructions are fine for the older versions. Since you installed Karmic as a new install you now have grub2 and the method to reinstall has changed. I hope you did not install grub legacy on top of grub2 as that makes it more difficult to recover.

Follow the version for grub2 with Karmic 9.10 or later.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
worked perfect thank you

---

