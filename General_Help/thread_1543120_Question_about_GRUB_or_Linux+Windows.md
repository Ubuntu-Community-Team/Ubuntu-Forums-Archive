---
title: "Question about GRUB or Linux+Windows"
date: 2010-07-31
forum: General Help
---

### Post by gabe17 on 2010-07-31
Hi there! I have installed Ubuntu 10.04 on my 500GB HDD. You can see how it is partitioned on the included screenshot. Now I've got a second HDD and I wan't to install Windows 7 on it (because I need to use some programs that go only on Windows). So now I don't know what to do...If I would install the Windows, It would eat my GRUB (I think)...so please give me an advice what to do (I'm quite a N00B, so I would be very thankful for a step-by-step instructions. Thanks. 

Note: Both discs are SATA.

---

### Post by WorMzy on 2010-07-31
Yes, installing Windows (any variety) will "eat" grub and install it's own bootlaoder to the MBR (master boot record). But you can reinstall grub afterwards by following this guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by gabe17 on 2010-07-31
Please, could you tell me exactly what I'm supposed to do?

---

### Post by WorMzy on 2010-07-31
I could, but I'd just be repeating what's already on the page I linked you to, and there's a chance that I'd forget something important.

---

### Post by Mark Phelps on 2010-07-31
> **gabe17 said:**
> Hi there! I have installed Ubuntu 10.04 on my 500GB HDD. You can see how it is partitioned on the included screenshot. Now I've got a second HDD and I wan't to install Windows 7 on it (because I need to use some programs that go only on Windows). So now I don't know what to do...If I would install the Windows, It would eat my GRUB (I think)...

MS windows always installs its own MBR to the "first" disk it finds.  So, in this case, to prevent overwriting GRUB, the process is very simple:
1) Disconnect the Ubuntu drive containing GRUB
2) Put the Win7 DVD in the drive and boot from it
3) Install Win7 to the only drive now connected
4) Reconnect the Ubuntu drive and boot from it -- NOT from the Win7 drive
5) Once into Ubuntu, run "sudo update-grub" from a terminal.  This will autogenerate a new GRUB2 menu and SHOULD add an entry for Windows 7.
6) Reboot your machine

You should now see a GRUB menu with entries for Ubuntu and an entry for Win7.

If you want to change the default order of the entries, install Startup-Manager in Ubuntu and use it to select which entry you want to be the default.  It will automatically run update-grub and regenerate the GRUB menu for you.

---

### Post by gabe17 on 2010-07-31
But point 4...that means that in one time I will have connected one drive with GRUB and one will MBR...isn't that a problem? How do I know that it will boot from the drive I want?

---

### Post by jerenept on 2010-07-31
set it in BIOS.

---

### Post by deserthowler on 2010-07-31
> **gabe17 said:**
> But point 4...that means that in one time I will have connected one drive with GRUB and one will MBR...isn't that a problem? How do I know that it will boot from the drive I want?

Make sure your BIOS is set to boot from the Ubuntu drive first.

Earl

---

### Post by gabe17 on 2010-07-31
Yea, I didn't realise it :) Now I now :) Thank everybody for help, will try it tomorrow and let know :)

---

