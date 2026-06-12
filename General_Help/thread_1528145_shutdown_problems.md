---
title: "shutdown problems"
date: 2010-07-10
forum: General Help
---

### Post by Dave Otter on 2010-07-10
I have to use "sudo shutdown -h now" .Is there anything I can do to be able to shutdown normally? 

    Thankyou.

---

### Post by mike555 on 2010-07-10
I have used this on older computers ;
 in terminal type ;
sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

sudo update-grub

---

