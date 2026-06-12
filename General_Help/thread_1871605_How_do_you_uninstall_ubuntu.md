---
title: "How do you uninstall ubuntu?"
date: 2011-10-29
forum: General Help
---

### Post by kartik1807 on 2011-10-29
i installed Ubuntu natty from LiveCD.I need to remove it and reinstall using Wubi .HELP PLEASE
I am not much of a geek.
(1)using WIN7 with dual boot
(2)NEED TO REMOVE GRUB
:confused::confused:

---

### Post by coffeecat on 2011-10-29
@kartik1807, I've moved your post out into its own thread. Please start your own threads.

---

### Post by The Cog on 2011-10-29
Moved to its own thread. 

Firstly you need to replace grub with a windows bootloader. A quick google for restoring the bootloader came up with this link that looks goot but I can't vouch for it: [http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

Once you have grub removed the PC booting stratight into windows, then you can go about deleting the old Ubuntu partitions - there are probably two of them. You can do this with an Ubuntu live CD, or probably with the win7 disk manager utilities. I think wtih the win7 utilities you can even expand the win7 partition again so that it occupies the whole disk.

---

