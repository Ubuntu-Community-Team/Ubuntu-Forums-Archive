---
title: "Suse 9.1 not shown in Grub2"
date: 2011-07-20
forum: General Help
---

### Post by FreaK2k on 2011-07-20
Hey I've installed Ubuntu 10.04LTS next to the Suse Partition. But when I start the Computer, Suse 9.1 is not shown.

I've already tried to do sudo update-grub(2) + grub-mkconf + Manually editing the 40_custom file :(

Nothing helped.

What information do you need and how can I fix this mess?

PS: I can acces the Suse Partition from Ubuntu (/dev/sda3)

---

### Post by szal on 2011-07-20
[COLOR=Green]sudo os-prober[COLOR=Black] doesn’t see the SUSE? If it does, run [COLOR=Green]sudo update-grub[COLOR=Black] afterwards, and all should be OK.

And you should make upgrading SUSE to a supported version (11.3 or later) your top priority, but that’s another story… :)
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by FreaK2k on 2011-07-20
Thats the strande thing, os-prober sees it, update-grub recognises suse and sais done, But then there's no entry :)

But now I've got further Information to add it manually:

It is installed at /dev/sda3/

The Bootloaderentry within Suse (Yast Config shows me this informations)

(hd0,0) vmlinuz root=/dev/hda3 vga=normal apic showopts
(hd0,0) /initrd


How can I now add this entry?



I found help in another Thread thx :) They're helping me here:
[http://ubuntuforums.org/showthread.php?p=11066806#post11066806](http://ubuntuforums.org/showthread.php?p=11066806#post11066806)
Sorry for double post

---

### Post by Habitual on 2011-07-20
This may help.
[http://opensuse.swerdna.org/susebootubuntu.html](http://opensuse.swerdna.org/susebootubuntu.html)

---

### Post by FreaK2k on 2011-07-20
The Problem is, that I'm running the Ubuntu Grub2 and would prefer to stay this way. The other OS is more than 8 Years old and what I read, this Version causes a lot of trouble.

---

### Post by FreaK2k on 2011-07-20
Thanks for the help!

---

