---
title: "How to create a folder where you can copy files to but you can't delete them after."
date: 2010-11-24
forum: General Help
---

### Post by nemonline on 2010-11-24
Hi,
i've been looking for a solution to a problem i'm confronting atm. I need to create a folder where ppl can copy files and i need to be sure that those files cannot be deleted after they are copied there. The folder will be accessed over network, and i need to be sure no one will delete somebody else's files.
Also i need to tell you that i'm working with regular users, so creating a folder for each user and chown/chmod-ing it won't do the trick(allready tried and ended up with a whole lot of files in the parent directory).
I also tried chattr +a but that doesn't allow them to write new files in the folder.

I'm lost, please help!:)

---

### Post by TeoBigusGeekus on 2010-11-24
See [this]("http://art.ubuntuforums.org/showthread.php?t=1109185") and [this.]("http://stackoverflow.com/questions/869536/linux-directory-permissions-read-write-but-not-delete")

---

### Post by nemonline on 2010-11-25
thank you! i'll see what i can do, and post back with the results.

---

