---
title: "Grub 2.0, removing boot entries"
date: 2010-07-18
forum: General Help
---

### Post by Pharanoise on 2010-07-18
Hi everyone,
i have installed Ubuntu on my computer together with Windows Vista (On different partitions), now my boot selection menu that comes with Grub, is the following:

[LIST]
[*]Ubuntu, with Linux 2.6.32-23 generic
[*]Ubuntu, with Linux 2.6.32-21 generic
[*]Memory test (memtest86+)
[*]Memory test (memtest86+, serial console 115200)
[*]Windows Vista (loader)(on /dev/sda1)
[*]Windows Recovery environment (loader)(on /dev/sda2)
[/LIST]
There is a strange behavior, "Windows Vista" entry doesn't actually load Windows Vista, it loads an Acer Backup Program, for unknown reasons. To successfully run Windows Vista, i have to select the "Windows Recovery environment" entry. Is there something i can do with this?

Anyway, my goal was to restrict the list to 2 entries: Ubuntu and Windows Vista, is it smart to do that?
If so, i took a look into the */etc/grub.d/* directory, like the Grub tutorial says, but i can't find all entries, i can only display those files:


[LIST]
[*]00_header
[*]05_debian_theme
[*]10_linux
[*]20_memtest86+
[*]30_os-prober
[*]40_custom
[*]README
[/LIST]
Which files should i edit/erase?
I'm quite confused :confused:

---

### Post by oustiti on 2010-07-20
There are a couple of good guides on configuring Grub 2 here :

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

and here :

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

