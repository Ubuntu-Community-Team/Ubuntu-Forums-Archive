---
title: "Customize install cd - disable main menu when ubiquity start"
date: 2009-09-16
forum: General Help
---

### Post by gdupasqu on 2009-09-16
Hello,

When customizing ubuntu livecd (mksquashfs, ....) and a preseed file accessed by isolinux.cfg, I would like to disable main menu when starting ubiquity.

In my preseed file, option are defined for language, time, partioning ... but still the main menu is displayed asking me to choose a language and so on. I would like to automatically skip those steps without typing anything from my keyboard.

The preseed file is well loaded since the language I have selected appears as default in the main menu.

Do I need to add an option in my isolinux.cfg file ?

For now I have the line:
LABEL test
  menu ^Test mode
  kernel /casper/vmlinuz
  append file=/cdrom/preseed/test.seed auto=true priority=critical boot=casper only-ubiquity initrd=/casper/initrd.gz quiet --

Thank you in advance for your help,

Guillaume

---

