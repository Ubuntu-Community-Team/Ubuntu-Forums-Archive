---
title: "Selecting vista in grub leads to windows boot manager"
date: 2009-11-19
forum: General Help
---

### Post by Sidneyaks on 2009-11-19
I just installed both vista and then karmic fresh on my laptop (made for vista). I previously had vista and hardy which worked flawlessly, but now when I boot up the system and try and load vista from grub it goes to the windows boot manager. I was wondering if there was a way to make it just load vista instead of going to the boot manager.

---

### Post by lisati on 2009-11-19
Did you previously use Wubi by any chance?

---

### Post by Sidneyaks on 2009-11-19
Yes I had. I had started it but didn't let it finish because I read there were a lot of problems with having an ext file system within ntfs. Whoops, my bad.

Is there an easier way to fix it other than re-installing both os's?

---

### Post by fluffman86 on 2009-11-19
Boot Vista, and check to see "Ubuntu" is listed in your Programs under Control Panel.  If so, uninstall it.

Then click start, type msconfig, right click on the item that shows up and selct run as administrator.

Flick to the boot tab, or just keep looking around until you can edit the boot.ini file.  From there, you can remove the Wubi listing and change the timeout to 3 if you have a recovery partition, or 0 if you don't.

---

### Post by Sidneyaks on 2009-11-19
Cool, thanks fluff. :D

---

