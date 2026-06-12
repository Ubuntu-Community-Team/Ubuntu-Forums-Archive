---
title: "dpkg in a read-only root filesystem"
date: 2012-09-26
forum: General Help
---

### Post by h113331pp on 2012-09-26
Good day, everyone:
    I used to install dpkg packages in my embedded arm board with a nand flash, and my initrd will mount all my entire root filesystem as aufs, and I can 'temporary' install dpkg packages.

    And recently I change my kernel and removed initrd, so now I have to mount aufs after boot in linux, and "/" can`t be mounted as aufs after this change, but the others(etc, var, usr etc...) still can mounted as aufs, and cause a big problem --- It can`t install any dpkg packages!

    When I type something like: "sudo dpkg -i udiskie_0.4.2-atrust1-1_armel.deb", and system will spill out the following:

dpkg: error processing udiskie_0.4.2-atrust1-1_armel.deb (--install):
 unable to securely remove '//..dpkg-tmp': Read-only file system

    This confuse me, I don`t think it need "/" writeable to install packages.Could someone please teach me why this happen? I will be so grateful. :(

---

### Post by h113331pp on 2012-10-02
I very appreciate actionparsnip`s help.it inspire me more clues
 I found a work arround, plus "--instdir=/tmp" will solve this issue, below is what I do:
 user@atrust-004CC8:/tmp$ sudo dpkg -i --instdir=/tmp ./udiskie_0.4.2-atrust1-1_armel.deb
(Reading database ... 25296 files and directories currently installed.)
Preparing to replace udiskie 0.4.2-atrust1-1 (using .../udiskie_0.4.2-atrust1-1_armel.deb) ...
Unpacking replacement udiskie ...
Setting up udiskie (0.4.2-atrust1-1) ...
user@atrust-004CC8:/tmp$
 but apt still need to find a way to set instdir like dpkg does.

---

