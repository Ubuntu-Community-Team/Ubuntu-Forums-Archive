---
title: "How to set boot to command line instead of GUI"
date: 2010-01-22
forum: General Help
---

### Post by jerome schatten on 2010-01-22
I need to be able to boot to the command line in Ubuntu 9.10 rather than the GUI. From there, after doing some tasks, I will need to get to the GUI. So,
1. What to set to force the boot to the command line?; and 
2. Will **startx** work to get me from te command line to the GUI -- if not, what will?

I want to actually boot to the command line, not invoke a virtual terminal from the GUI.

Thanks,
jerome

---

### Post by sisco311 on 2010-01-22
In the /etc/default/grub file edit the GRUB_CMDLINE_LINUX_DEFAULT line to look like this:
```
...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **text**"
...
```

then run:
```
sudo update-grub
```

startx should work, if not try to start gdm: *sudo initctl start gdm*.

---

### Post by jerome schatten on 2010-01-22
Mul&#355;umesc  -- that worked fine!
Jerome

---

