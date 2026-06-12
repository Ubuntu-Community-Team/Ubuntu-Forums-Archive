---
title: "Keyboard stops working at LUKS prompt"
date: 2011-01-23
forum: General Help
---

### Post by pieterberlijn on 2011-01-23
I am running into a couple of problems. It seems that (after an update?) the keyboard modules for my Macbook fail to load in initramfs. I am able to use the keyboard during the grub menu, however, when prompted for my encryption passphrase,  I am unable to enter any characters.

A google search prompted the following bug (which seems outdated): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/310460](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/310460)

It seems that a hid-module is not loaded by initramsfs. I however am at loss how to edit my initramfs configuration without being able to boot into the system. Is there any way to do this from the grub prompt? Has anyone ran into this issue before?

---

