---
title: "new boot added to my bootup?"
date: 2012-01-02
forum: General Help
---

### Post by todd500 on 2012-01-02
I have windows 7 and I added a Ubuntu partition today and  after I did the security updates and restarted (in Ubuntu),there is a new Ubuntu selection in the boot loader .now I have 2 Ubuntu things in my boot loader. why did it do this and is this normal?

---

### Post by drs305 on 2012-01-02
The additional entry could be a newer kernel than the one on the original installation. As kernels are added during updates, they are included in the Grub menu. In the latest versions of Grub, rather than expand the main menu the older kernels are hidden in a submenu.

It's best to keep at least one older kernel that you know works in case you have problems with the latest one.

If you really want to remove these extra kernels from the menu, you can physically uninstall the older kernels or just hide them from the menu. An app called Grub Customizer can hide them, while Ubuntu Tweak can remove them from your OS.

You can get information on Ubuntu Tweak and other ways to remove/hide the kernels in this thread:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

For more on Grub Customizer, click the link in my signature line.

---

