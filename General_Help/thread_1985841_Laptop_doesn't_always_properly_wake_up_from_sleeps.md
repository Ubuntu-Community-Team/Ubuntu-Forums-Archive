---
title: "Laptop doesn't always properly wake up from sleep/suspend"
date: 2012-05-23
forum: General Help
---

### Post by Inhumane on 2012-05-23
Sometimes (about 1 out of every 10 times) when I put my laptop to sleep, it will come back on but the would only contain my mouse cursor (which I can move around) and nothing else, just a sort of very tiny checkboard/dots background, and it will stay that way until I manually shut off the computer and turn it back on. It happened on two seperate installations (but on the same laptop).

The video card if it matters is Intel 945GM

---

### Post by Inhumane on 2012-05-24
Anyone?

---

### Post by 2F4U on 2012-05-24
Can you provide more information about your laptop hardware, graphics card and graphics driver you are using? Also, when it fails to resume there is a log file /var/log/pm-suspend.log. Look into this file and search for errors.

---

### Post by Inhumane on 2012-05-24
I'll check into that log file when it happens, good to know. Although it's really long.. hopefully it'll be of some help.

The laptop is X61s. As mentioned in the OP it is 965GM/X3100 graphics and I'm not sure what graphics driver it's using. Although honestly I'm positive it has nothing to do with the graphics driver. It's a resuming from sleep issue. It isn't able to reinitialize X or I don't know what, but it can't load something to proceed to the full desktop

---

### Post by 2F4U on 2012-05-24
The 965GM is an Intel chipset and therefore Ubuntu is using the open source Intel driver. There is no proprietary driver available. I quickly looked through this site for known problems on that hardware, but couldn't find anything:

[http://www.thinkwiki.org/wiki/Category:X61](http://www.thinkwiki.org/wiki/Category:X61)

Thinkpads are usually highly compatible to Linux. I own a T60 and it basically runs every Linux distribution I install on it.

---

### Post by LawM on 2012-05-24
I've been having tons of issues with this graphic card. I fixed most of them by adding this to the boot line:

acpi_osi= Linux acpi_backlight=vendor

To try if it works, during grub time add that after "quiet splash" and boot.

With that I got my suspend and hibernate back.

If it works, as a definite solution, modify the file /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

and run update-grub2.

Anyway, I did that and I was happy back to restarting, hibernating and suspending my laptop. However, when I updated the xorg-server, i had to remove that lines to make all those functions work again, I guess they fixed the issue, so try adding/removing and see if they work.

---

