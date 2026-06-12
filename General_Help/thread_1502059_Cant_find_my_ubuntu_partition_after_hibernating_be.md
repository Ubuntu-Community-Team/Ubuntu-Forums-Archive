---
title: "Cant find my ubuntu partition after hibernating before i installed debian"
date: 2010-06-05
forum: General Help
---

### Post by topbyter on 2010-06-05
Hey can anyone help me? I was having xp on one partition and ubuntu on another partition. i decided to installed debian on one of the xp partition but before i installed the debian(lenny) i forgot i hibernated ubuntu instead of proper shutdown. now i can seem to get my ubuntu in grub. even when i try to mount the partition it says:
mount: /dev/sda5 already mounted or /mnt busy

please i need an urgent help. i have a completed project on the ubuntu that i am supposed to passed to the client today. My office will kill me if they discover.

---

### Post by wojox on 2010-06-05
Does it see Debian?

Try reinstalling grub [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by egalvan on 2010-06-05
Hibernation uses the SWAP partition.
When you installed  Debian, it found that swap partition, and most likely formatted it, thus wiping your hibernated OS.
note: you haven't actually "lost" anything, just a "snapshot" of the OS and data that were in RAM at the moment of hibernation...
unless you were working on some file,,, but most software automatically makes backups... "~" files, and that should still exist.


The hibernation flag needs to be reset, but I don't have a clue how that is done.
Hopefully some other wizard will show up :)

---

### Post by topbyter on 2010-06-06
Hey guys...thank you for your contributions. they were really helpfull for knowledge sake. I ran testdisk package on the installed debian. it recovered both my NTFS formatted partition and my ubuntu partition.

However i lost the files that where opened as at the time of hibernation. no worry. i am glad.

God bless you guys.

---

