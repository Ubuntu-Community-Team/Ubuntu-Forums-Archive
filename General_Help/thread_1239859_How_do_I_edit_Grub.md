---
title: "How do I edit Grub"
date: 2009-08-14
forum: General Help
---

### Post by chris1950 on 2009-08-14
I installed a server kernel and lost all my networking (wireless and Lan). When Grub starts I hit esc it gives me the option to boot using generic. When I did all my networking came back. I need to change Grub to use the generic setting by default not the server.

---

### Post by sonu 1807 on 2009-08-14
Install start-up manager from Add/Remove and then choose the default in the Boot options

---

### Post by mthalis on 2009-08-14
[http://ubuntuforums.org/showthread.php?t=169234](http://ubuntuforums.org/showthread.php?t=169234)

---

### Post by pastalavista on 2009-08-14
If you aren't going to run the server kernel, you should remove it. Open System > Administration > Synaptic Package Manager. Click the 'Installed' button in the left panel and then search for 'linux-image'. Right-click the 'server' kernel and select 'remove completely' and reboot

Or you can use the terminal (Applications > Accessories > Terminal)
and enter this ```
gksu gedit /boot/grub/menu.lst
```
At the bottom you'll see a list of kernel titles. The top title is '0'. The second is '1' etc. At the top of the page (a few lines down) is an entry 'default' with, uually a '0' after it. Change the '0' to the generic kernel number, probably '2'. Or you can just add a comment notation '#' at the beginning of the line to make it not active. Then reboot.

---

### Post by chris1950 on 2009-08-14
Thanks guys. It wasn't listed in startup manager so went to Terminal using sudo su edited Grub by deleting the two serve enteries, saved, rebooted and everything works fine ,am now using laptop to post this reply.

---

