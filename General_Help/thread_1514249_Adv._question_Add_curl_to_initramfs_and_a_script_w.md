---
title: "Adv. question: Add curl to initramfs and a script which uses it"
date: 2010-06-20
forum: General Help
---

### Post by tnek on 2010-06-20
Hi,

I am trying to learn how to modify the initramfs in a way which is so Ubuntu-friendly as possible. I do not just want to unpack it, change it and re-pack it, as my changes won't be kept when I upgrade my kernel next time.

What I want to do is:

[LIST]
[*]Add curl to the binaries available in the initramfs
[*]Add a script which is run after networking is set up which calls curl
[*]In case there is no "after networking" I have to setup networking myself using DHCP. There is a tiny client inside BusyBox if I am not mistaken.
[/LIST]
I have googled **a lot** to get this information. As well as looked trough more than a few books. Any help or a pointer to some information which describes something similarly would be very much appreciated!

---

### Post by Bachstelze on 2010-06-20
Is your networked configured through networkmanager, or through /etc/network/interfaces? In either case, you shouldn't have to modify the initrd, the filesystem should be available way before the network is up (otherwise, where would the OS get the necessary information for bringing the network up?).

---

### Post by tnek on 2010-06-21
What I am really trying to do is:

[LIST]
[*]Learn how initramfs works (I don't think initrd is used any more, despite the name of the file in /boot and the menu entry in GRUB)
[/LIST]

[LIST]
[*]Create a way in which I may log in using SSH and type in the password for my encrypted LVM-device.
[/LIST]
The last one defenitely requires messing with the initramfs. But thank you for replying and trying to help!

---

