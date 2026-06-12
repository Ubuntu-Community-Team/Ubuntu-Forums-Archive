---
title: "Reinstalling GRUB boot loader."
date: 2006-05-01
forum: General Help
---

### Post by k00zk0 on 2006-05-01
I originally had Windows XP and Ubuntu installed using GRUB (provided with Ubuntu) and it booted both OS'es normally.

I made a 4th partition to install a distro called Backtrack (for security auditing) and it hijacked my bootloader and replaced it with LILO, forcing that distro to always boot instead.

All I need to do is reinstall GRUB with all the entries i had before in it and the new distro also (I can edit the config myself after so its not a problem).

I googled it and I cant get any methods to work.. including direct directions to type 'grub-install /dev/hda' at the rescue prompt of the first CD of Red Hat 9. Whatdayathink. Command not found. What the hell?

---

### Post by PhoenixP3K on 2006-05-02
That's some weird case. I was going to propose '[grub-install /dev/hda]("http://easylinux.info/wiki/Ubuntu#How_to_restore_GRUB_menu_after_Windows_installation")' with the Ubuntu CD rescue as root... have you checked if your first booting harddrive is really /dev/hda ? For example if your hard drive connects via SATA it will be /dev/sda
You could always look for info on how to change the default boot in LILO since Ubuntu can install LILO also.

---

### Post by r4ik on 2006-05-02
You could give this a read,

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Good luck !

---

