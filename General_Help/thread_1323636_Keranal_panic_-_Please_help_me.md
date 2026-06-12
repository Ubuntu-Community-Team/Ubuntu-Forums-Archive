---
title: "Keranal panic - Please help me"
date: 2009-11-11
forum: General Help
---

### Post by mthalis on 2009-11-11
I installed ubuntu 9.10 inside windows. last night I properly shut down my computer(ubuntu os). but now I can't logging ubuntu it issue below error message.
**Kernel panic -not syncing vfs: unable to mount root fs on unknown block(8,7)**

please help me solve this problem.

Note- I can't format ubuntu because important data is in my ubuntu partition.

---

### Post by Sin@Sin-Sacrifice on 2009-11-11
You need to specify where to mount the root FS in grub.conf. I'm not real familiar with all this but [http://forums.fedoraforum.org/archive/index.php/t-31372.html](http://forums.fedoraforum.org/archive/index.php/t-31372.html) this shows some insight on the matter. It looks like putting mkinitrd at the end of the boot command should do you right. Otherwise check the grub.conf file via the boot disk and change "root=LABEL=/" to "root=/dev/whereyourrootissupposetomount" Mine is "root=/dev/sdb2" for example. Hope this helps.

---

### Post by mthalis on 2009-11-11
Thanks for reply. How can I edit grub.conf, because I can't go ubuntu partition . I installed ubuntu using Wubi. I also want to protect my both windows and ubuntu partition.

---

### Post by Unanimated on 2009-11-11
If you installed it using Wubi, then you can navigate through Ubuntu's folders in the Wubi folder in Program Files or somewhere like that, then simply uninstall Wubi and reinstall it again if you want to keep Ubuntu. If you leave it uninstalled, then check the Wubi website for instructions - Ubuntu will still show up on the boot menu, even though it doesn't exist. I'm sure the site has instructions on how to get rid of that.

---

### Post by Sin@Sin-Sacrifice on 2009-11-11
You can access the partition through the boot disk. Restart the PC with the boot disk in and select "Try ubuntu without installing". Then you can navigate to the folder and open grub.conf with your favorite text editor. You are probably going to need root privs so you might want to "sudo gedit" the file from the terminal. I know nothing of wubi or whatever it's called. Never used it...

P.S. I wish someone more knowledgeable would intervene because I don't think Karmic (grub1.97) has a grub.conf file now that I looked. The "root=" stuff was from memory from Jaunty.

---

