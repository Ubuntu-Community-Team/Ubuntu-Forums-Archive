---
title: "Grub stopped working"
date: 2010-03-29
forum: General Help
---

### Post by Fragger123 on 2010-03-29
Hello there,

After I installed Windows XP on my leftover partition, I decided to reinstall grub2.

Now when I reboot grub throws me in the grub shell, if I then type configfile /grub/grub.cfg it starts grub like its supposed to. Tho I cant seem to be able to go straight to the grub menu and no to the shell.

---

### Post by Brandon Williams on 2010-03-30
Did you reinstall grub2 from the installed ubuntu or from a live CD? I've seen the behavior you describe after making a mistake when reinstalling grub from a live CD, and resolved it by booting all the way into the installed system and running 'sudo grub-install' from the command line.

---

