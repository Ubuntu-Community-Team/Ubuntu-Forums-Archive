---
title: "Two entries for the same kernel version in GRUB?"
date: 2010-05-10
forum: General Help
---

### Post by mahela007 on 2010-05-10
I have two entries for the same kernel version in GRUB. I'm using the kernel supplied with 10.04. There are two entries for normal booting and two entries for safe mode.. so altogether 4 entries for the same kernel. 
If it's relevant , when I upgraded, I chose to install GRUB on all the partitions because the installed told me that that was the best option if I didn't know which partition was set to boot by the BIOS>

---

### Post by philinux on 2010-05-10
Yes thats normal. I always keep 2 kernels, plus recovery mode so thats 4 entries. You only need to hit the enter key to boot the first entry.

If you dont like the clutter you can remove old kernels via synaptic.

---

### Post by mahela007 on 2010-05-10
that's the problem. Both entries refer to the same kernel version.

---

### Post by philinux on 2010-05-10
> **mahela007 said:**
> that's the problem. Both entries refer to the same kernel version.

Ok lets have a look. In a terminal. Copy and then paste in the following command

```
cat /boot/grub/grub.cfg  | grep menuentry
```

When you post back the output wrap code tags around it.

---

### Post by sedawk on 2010-05-10
When the grub menu is visible you can also edit the
entries. When entering the "edit" mode you also
see all the parameters. There might be a difference
in the parameters you do not see from grubs main menu.

---

### Post by mahela007 on 2010-05-11
> **philinux said:**
> 
```
cat /boot/grub/grub.cfg  | grep menuentry
```.
```

menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {

```

---

### Post by oldfred on 2010-05-11
It looks like you did an upgrade from Karmic.

You have 2.6.[COLOR=Red]31[/COLOR]-21 from Karmic and 2.6.[COLOR=Red]32[/COLOR]-21 from Lucid. They both happened to have the last -21 the same at the time you did the upgrade.

---

### Post by mahela007 on 2010-05-11
Oh.. So I can just go ahead and uninstall them from synaptic if I want to?

---

