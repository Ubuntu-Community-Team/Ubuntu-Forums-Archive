---
title: "Best way to password protect a folder on a flash drive?"
date: 2010-09-03
forum: General Help
---

### Post by JohnElway on 2010-09-03
I have a folder on my flash drive where I keep sensitive info (important numbers, passwords, etc.) and would like to protect this info in the event that someone gets a hold of this drive.

I figured the best method was encryption so I started experimenting with gpg, but I encountered problems as mentioned here:

[http://ubuntuforums.org/showthread.php?t=1567025](http://ubuntuforums.org/showthread.php?t=1567025)

I still haven't found a solution so I'm looking into possible alternatives. As shown in the above thread, someone recommended using eCryptfs or an  encfs directory. Before I spend anymore time researching this stuff, has anyone tried using these before? Do they work well and do you think these would suit my needs?

The only other alternative I can think is just compressing the folder into a password protected rar file. Would this work well or would I be leaving my data vulnerable?

ALSO, I would a prefer a solution that would still allow me to backup this folder using rsync. I like to keep and up-to-date backup of my entire flash drive by syncing it to another flash drive using rsync.

---

### Post by TimEnid on 2010-09-03
i use truecrypt to protect files that i dont want viewed by others. it creates a partition on your hd and you can store your sensitive info in there. its impossible for someone to access it without the password.

---

### Post by JohnElway on 2010-09-05
For anyone viewing this, I decided to go with EncFS and so far, it seems like the perfect solution for what I'm trying to do. If you're curious about how EncFS compares to other encryption methods, like TrueCrypt, and how to install it, check out [http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/). And if you're interested in using it with a GUI, there's an app in the repositories called CryptKeeper, although I haven't tried it.

---

