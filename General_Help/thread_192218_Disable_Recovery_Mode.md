---
title: "Disable Recovery Mode?"
date: 2006-06-08
forum: General Help
---

### Post by hxx4 on 2006-06-08
I'm curious as to if there is a way to fully disable recovery mode in ubuntu. I'm not posting to discuss the practicality or security implications of doing so, and I already know how to password protect the recovery mode entry and interactive editing in grub. But you can still boot from the install CD into recovery mode, and I'm not interested in password protecting the bios and changing the boot order. So can it be done?

---

### Post by kaamos on 2006-06-08
> But you can still boot from the install CD into recovery mode

Well, even if you could disable the recovery mode completely, without bios password (which can often be reseted by removing the battery..) one could just boot with any live cd and mount your hard drive. If one has physical access to the machine, the only thing that really matters is: are the hard drives ecrypted or not?

---

### Post by compmodder26 on 2006-06-08
[http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_disable_all_interactive_editing_control_for_GRUB_menu]("http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_disable_all_interactive_editing_control_for_GRUB_menu")

EDIT: Just re-read your post, I see you know how to do this already.  What you are looking for can only be accomplished via the bios (ie. by password protecting bios and changing boot order, which you say you don't want to do).

---

### Post by hxx4 on 2006-06-08
[QUOTE=compmodder26][http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_disable_all_interactive_editing_control_for_GRUB_menu]("http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_disable_all_interactive_editing_control_for_GRUB_menu")

EDIT: Just re-read your post, I see you know how to do this already.  What you are looking for can only be accomplished via the bios.[/QUOTE]

All I'm really interested in is disabling recovery mode, and I understand there are  other ways to get access to the hard drive (through a live CD). But disabling recovery mode would prevent anyone from getting quick and easy command line access to the system.

---

### Post by aysiu on 2006-06-08
[QUOTE=hxx4]All I'm really interested in is disabling recovery mode, and I understand there are  other ways to get access to the hard drive (through a live CD). But disabling recovery mode would prevent anyone from getting quick and easy command line access to the system.[/QUOTE] Maybe this is dumb, but can't you just delete the Grub entry for it?

---

### Post by hxx4 on 2006-06-08
[QUOTE=aysiu]Maybe this is dumb, but can't you just delete the Grub entry for it?[/QUOTE]

You can still boot into recovery mode from the ubuntu install CD.

---

### Post by thasheep on 2006-06-08
[QUOTE=aysiu]Maybe this is dumb, but can't you just delete the Grub entry for it?[/QUOTE]
You could but it'd re-appear the next time update-grub were run. However, you can change the line in /boot/grub/menu.lst
```
# alternative=true
```
to
```
# alternative=false
```
Make sure you keep the (one) #
then
```
sudo update-grub
```
This will remove the recovery mode boot options. You might also want to set a password in menu.lst so that people can't interactively edit the boot options.

---

### Post by handydan918 on 2008-03-18
Someone will have to explain to me why toggling a true/false value to the right of a comment (#) makes any difference at all...

---

### Post by markharding557 on 2008-03-18
> **hxx4 said:**
> I'm curious as to if there is a way to fully disable recovery mode in ubuntu. I'm not posting to discuss the practicality or security implications of doing so, and I already know how to password protect the recovery mode entry and interactive editing in grub. But you can still boot from the install CD into recovery mode, and I'm not interested in password protecting the bios and changing the boot order. So can it be done?

the only way to get the security level you want is to:
1 password the bios
2 encrypt the file system
this is complicated to do on an existing installation but is quite easy on a new install if you use the ubuntu alternate install cd,this uses a text installer which has options for creating a lvm or lvm encrypted partition.
when a partition is encrypted it cannot be accessed by a live cd and can only be booted into using the password you set.
edit: iv'e realized that a bios password will not prevent the harddisk being read in a different pc

---

### Post by az on 2008-03-18
> **hxx4 said:**
> But you can still boot from the install CD into recovery mode, and I'm not interested in password protecting the bios and changing the boot order. So can it be done?

You can have full and complete access to your filesystem by booting from a live cd.  You don't even have to boot into that system.

There is no way to "dissable" that.  It's a fact of life.  Anyone with physical access to your computer can become root.  As mentioned, encryption is the only option that would be effective.


> **handydan918 said:**
> Someone will have to explain to me why toggling a true/false value to the right of a comment (#) makes any difference at all...

When grub boots, it reads the menu.list file.  Comments are ignored.  The update-grub script, is different.  Commented lines have a different meaning and you can set options to automagically configure all the gub stanzas at once.  Read the actual menu.list file for more information.

---

