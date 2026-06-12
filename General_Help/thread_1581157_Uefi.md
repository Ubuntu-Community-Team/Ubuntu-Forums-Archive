---
title: "Uefi?"
date: 2010-09-24
forum: General Help
---

### Post by Espionage724 on 2010-09-24
My motherboard supports UEFI boot, and from what I can understand, I simply choose the efi file to boot from, and it happens (I choose bootx64.efi for the win7 x64 dvd to install win7 in efi mode)

Does ubuntu have such a thing? I read in several places that I would have to install refi or something, and then compile stuff, and I wasn't tooooo sure about this.

---

### Post by searchfgold6789 on 2010-09-24
Yeah probably.
It shouldn't be that hard...should it?

---

### Post by Espionage724 on 2010-09-24
> **searchfgold6789 said:**
> Yeah probably.
It shouldn't be that hard...should it?

My thoughts exactly, but seeing the pages about UEFI and Ubuntu seems to suggest otherwise.

I'll actually try UEFI booting a Ubuntu x64 CD and see what happens.

---

### Post by searchfgold6789 on 2010-09-24
Sure, see what happens.

---

### Post by Espionage724 on 2010-09-24
Na theres no efi boot file on the x64 disc :(

I hear fedora has one though, if I heard correctly that is.

Can anyone shed light as to how to install Ubuntu in EFI/UEFI mode?

---

### Post by srs5694 on 2010-09-24
I don't have any UEFI-capable machines, but I did locate [this page](https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel) with some information. It's a Mac-centric page, but I imagine many of the issues would be the same for a UEFI-based non-Apple PC.

I just checked a few Linux install images I've got, and it looks like Fedora (at least, Fedora 13 beta) does include EFI boot support -- at least, there are some promising-sounding files. There's also a boot/x86_64/efi file on an OpenSUSE 11.3 DVD image I have handy. Thus, if Ubuntu's giving you trouble, you might try one of those.

One caveat: At least on BIOS-based systems, OpenSUSE seems to like converting GPT disks into GPT disks with [hybrid MBRs.](http://www.rodsbooks.com/gdisk/hybrid.html) If it does the same thing on UEFI-based systems, that could be bad news for Windows. This problem is correctable with [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) and probably other tools. In gdisk, you'd type "x" to enter the experts' menu, then type "n" to create a new protective MBR, then type "w" to save your changes.

---

