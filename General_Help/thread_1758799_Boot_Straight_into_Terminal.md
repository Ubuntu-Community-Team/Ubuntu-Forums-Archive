---
title: "Boot Straight into Terminal?"
date: 2011-05-15
forum: General Help
---

### Post by jimford on 2011-05-15
I'm using a low spec machine and want to run it 'headless', so I don't need a GUI and want to conserve resources.

How do I boot straight into a terminal session, rather than a GUI, please?

Jim

---

### Post by wgarcia on 2011-05-15
Step 1:Just edit /etc/default/grub with your favourite editor:

    sudo gedit /etc/default/grub

find out this line:

    GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”

change it to:

    GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”

Step 2:
Update grub and done!

    sudo update-grub

(From: [http://ubuntuguide.net/boot-into-consolecommand-line-when-startup-ubuntu-9-10](http://ubuntuguide.net/boot-into-consolecommand-line-when-startup-ubuntu-9-10))

---

