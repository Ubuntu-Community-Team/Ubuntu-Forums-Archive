---
title: "HELP! Grub can't see anything!!"
date: 2010-11-16
forum: General Help
---

### Post by Tryfon on 2010-11-16
Ok, I have a new Asus Eee Pc 1215n and installed on it Ubuntu 10.10. This way it was configured as dual-boot with 4 partitions. One for Windows7 one for Windows recovery, one for Linux swap and one ext4 for Ubuntu.
Everything was working fine until I installed the ext2fsd driver on Windows. It couldn't read the ext4 partition properly so I played with the options. There I tried changing the ext partition's type from "Linux" to "Linux extend" (which was obviously wrong). After the reboot I get a message when the computer starts up saying "error: partition not found" and in the next line "grub rescue>" with a dash flashing but without any recognizable commands.
I tried reinstalling grub from the Ubuntu 10.10 live cd following [these]("http://ubuntuforums.org/showthread.php?t=1581099&highlight=reinstall+grub") instructions but now I get exactly the same screen, this time saying "error: file not found." instead. What was weird was that gparted in the live Ubuntu couldn't see **any** partition in the hard drive. It appeared like the whole space was unallocated.
When I type 'help' in "grub rescue" it tells me "unknown command". 
When I type ls it returns: (hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
I think this might be a clue of what is going on since all the partitions should not be flagged as msdos.

Help please! I don't want to reinstall everything!

---

### Post by psusi on 2010-11-16
Don't duplicate post:

[http://ubuntuforums.org/showthread.php?t=1623299](http://ubuntuforums.org/showthread.php?t=1623299)

---

