---
title: "Booting without starting gdm"
date: 2011-11-02
forum: General Help
---

### Post by muphrid15 on 2011-11-02
I'm trying to boot to a command line without starting GDM.  I've tried setting GRUB_CMDLINE_LINUX_DEFAULT="text" in /etc/default/grub.  I've tried adding /etc/init/gdm.override (with the only text of the file "manual").  I've tried moving /etc/init/gdm.conf altogether, yet gdm always starts.

Is this even possible to do still?

---

### Post by oldos2er on 2011-11-03
See [http://ubuntuforums.org/showthread.php?p=11417839](http://ubuntuforums.org/showthread.php?p=11417839) (assuming you're using 11.10).

---

### Post by muphrid15 on 2011-11-03
Worked, thanks!

---

