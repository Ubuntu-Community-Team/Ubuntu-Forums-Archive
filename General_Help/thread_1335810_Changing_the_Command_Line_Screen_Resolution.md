---
title: "Changing the Command Line Screen Resolution"
date: 2009-11-23
forum: General Help
---

### Post by milawynsrealm on 2009-11-23
When using Ubuntu back on my backup desktop computer, I had downloaded some sort of GUI GRUB configuration tool (I'm not quite sure which one it was). When I had switched to Console-Only mode, the text was smaller and I liked it. But now I had to do a clean install to the latest Ubuntu version and the tool is now gone.

If you don't know what tool I'm talking about, then can you at least explain which configuration file to edit? The default resolution is okay, but I want a better one.

---

### Post by bmorency on 2009-11-23
give this site a try. You have to add vga=xxx to the kernel line in the config file. The 'xxx' is the resolution from the table.

[http://manac.wordpress.com/2006/02/19/how-to-change-grub-menu-resolution/]("http://manac.wordpress.com/2006/02/19/how-to-change-grub-menu-resolution/")

 You have to make a change in the file /boot/grub/menu.lst

---

### Post by falconindy on 2009-11-23
Not only does Karmic not have a menu.lst, but the vga= parameter **does not work** with grub2. [This post](http://ubuntuforums.org/showpost.php?p=8024427&postcount=17) details what you want to change.

---

