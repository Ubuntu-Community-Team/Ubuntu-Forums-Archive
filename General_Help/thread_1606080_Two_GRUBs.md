---
title: "Two GRUBs"
date: 2010-10-26
forum: General Help
---

### Post by Unfrog on 2010-10-26
Hello, I'm in need of some advice, but let me explain the situation first.

 I currently have 3 systems on my laptop: slightly bugged fedora, which I keep in case something breaks the partition with: Windows7 and Ubuntu (installed with Wubi, which means they're on the same partition, right?). I have two GRUBs at the moment. One that points to either Fedora, or the windows OS launcher. The windows OS launcher points to windows7 and the second GRUB that starts my Ubuntu. So to use my main OS (Ubuntu) I have to go through 3 OS loaders. Ubuntu only 'knows' about the second one and that's the one it updates if it needs to. I don't have the BIOS admin password, so I don't want to mess with partitions or the first GRUB, other than changing it's options files.

I would like to have the first GRUB point to Ubuntu by default. I could just edit it's options, but if I the kernel or any of it's arguments get updated, I might not notice and I don't really want to do it every time something changes. Is there any way to tell Ubuntu to update two GRUBs? Or better yet, update the options files, but leave the 'first' GRUB's internal files as they were (I don't want it to be updated, just in case something doesn't work with the update).

---

### Post by dcstar on 2010-10-26
Grub works by have a tiny bit of boot code pointing to where you have the main Grub files (in the /boot folder) - the boot code exists on whatever partition has the boot flag set (and therefore the BIOS boots it up).

You should be able to have multiple Grub installs and have the first Grub essentially "jump" to those via manually set up menu entries in the first Grub system, but it could get complicated.

It is much simpler not to have Ubuntu installed inside Windows but have it as a normal, stand alone, partition with its Grub directly controlling the booting of all other OSs in the system.

---

### Post by Unfrog on 2010-10-26
Umm... thanks, but that's not really what I was looking for. I know I can manually set up the first GRUB to point to my Ubuntu, and I will do that if I can't find a way to automate it. I want to automate it, so any updates are included there, even if I don't manually update it. I want Ubuntu to manage it's own (second) GRUB, and update the options files (and only the option files!) in the second. This way if Ubuntu updates it's GRUB and fails, I won't be left with a laptop that doesn't boot.

And I can't currently install Ubuntu on a stand-alone partition. I would've done that if I could.

---

### Post by oldfred on 2010-10-26
Wubi only boots thru the windows boot loader and is inside the windows NTFS partition. You then cannot combine its boot into the Fedora boot that you are using. Even if you installed Ubuntu into separate partitions, you could not get it to automatically update Fedora's grub. Each grub works on its own.

Why cannot you install Ubuntu to a partition? Linux installs just fine to logical partitions inside an extended partition and can be just as small as the wubi install?

---

### Post by Unfrog on 2010-10-26
Not having a BIOS admin password means I'm not messing with my partition layout, because if something goes wrong, I can't boot a live CD and restore things. I can't afford to have this computer not working for that long, at least not until Christmas.

It's bad news that I can't have the fedora's GRUB point to Ubuntu. I guess I will just have to sit there through all the bootloaders and press enter until it loads.

Thanks for your replies.

---

