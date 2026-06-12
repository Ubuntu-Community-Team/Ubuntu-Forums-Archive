---
title: "Dual booting with windows(Need easiest way)"
date: 2006-05-11
forum: General Help
---

### Post by Rahu on 2006-05-11
I'm looking for the simplest way to install a dual boot of ubuntu/windows on a blank hard-drive. I'm completely new to this, and couldn't find help by searching. If there is a thread i missed or a tutorial I would really appreciate a link.

I saw a few threads, but none that were a straight forward way to do it.

Thanks for any help :)

---

### Post by Sef on 2006-05-11
Here's an excellent tutorial on dual booting.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by tonyr on 2006-05-11
Here's a good place to start.  I'm not sure it says this, but always install Windows
first.   Don't use all of the drive for the Windows partition.
[URL="http://users.bigpond.net.au/hermanzone/"]
http://users.bigpond.net.au/hermanzone/[/URL]
(thanks to aysiu, who seems to have links to everything)

---

### Post by drpepper on 2006-05-11
yeah what tonyr said is right, always install windows first. this is because its worse at handling the boot sector than linux is. linux will adapt around windows, but not visa ve. when you install windows make sure u leave enuf unpartitioned space room for the linux to install.

another tip, that i ended up doing was creating a 3rd partion, in fat32. (and older filesystem). this was so both windows and linux had a common ground they cud share files between. coz windows cant read linux partitions and linux scruggles with ntfs partitons.

---

### Post by drpepper on 2006-05-11
yeah what tonyr said is right, always install windows first. this is because its worse at handling the boot sector than linux is. linux will adapt around windows, but not visa ve. when you install windows make sure u leave enuf unpartitioned space room for the linux to install.

another tip, that i ended up doing was creating a 3rd partion, in fat32. (and older filesystem). this was so both windows and linux had a common ground they cud share files between. coz windows cant read linux partitions and linux scruggles with ntfs partitons.

---

### Post by Rahu on 2006-05-11
Alright, I'm having a problem now. i tried doing it like that, but with the dapper beta. Now grub complains whenever i start the computer.

"18 : Selected cylinder exceeds maximum supported by BIOS"

It's a new install, so I'm willing to redo either installation, but what would i do differently to avoid this?

ps, I found one before I saw that guide, so I used [http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#installonnewhdd](http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#installonnewhdd)

---

### Post by tonyr on 2006-05-11
This must be a really old machine, or a really old BIOS.  It might be that this can only
fixed by upgrading the BIOS: find out what your BIOS is, find the newest
update if there is one, flash to new BIOS into ROM,  BE VERRRYYYY CAREFUL!

---

