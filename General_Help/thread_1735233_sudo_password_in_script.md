---
title: "sudo password in script"
date: 2011-04-21
forum: General Help
---

### Post by Rob8900 on 2011-04-21
Hi,

I have following script to avoid the typing of the sudo password  :

[I]echo 'x' | sudo reboot
[/I]

This script worked in XUbuntu 8.04, but does not work anymore in XUbuntu 10.10.

What do I wrong?


Best Regards,

Rob

---

### Post by Rob8900 on 2011-04-21
OK, I found the solution :

echo 'x' | sudo **-S** reboot

---

