---
title: "can't chmod /media??"
date: 2012-05-21
forum: General Help
---

### Post by upjeeper on 2012-05-21
i've got a 2nd hard drive that falls under /media which i'd like to chmod so i can allow other accounts in my group access to the files

i've tried everything from "sudo chmod..." to "sudo su" then "chmod", to opening the folder in the GUI
nothing seems  to want to let me change the permissions

any idea?

---

### Post by papibe on 2012-05-21
Hi upjeeper.

If the disk is NTFS formatted, that won't work since that filesystem doesn't support neither users or permissions.

The way you can do it is setting appropriate mount options, so it will be accessible for anybody.

Hope that helps, and tell us how it goes.
Regards.

---

### Post by upjeeper on 2012-05-21
ah. that would make sense.
where can i learn about the mount options?

the easy fix would be to copy my music to another directory, but that's a bit redundant.

and thank you for the quick response!!

---

### Post by papibe on 2012-05-21
Check post #8 on this [thread]("http://ubuntuforums.org/showthread.php?t=1204763").

The most important options is **umask=000**.

Regards.

---

### Post by upjeeper on 2012-05-21
i installed NTFS-config and used that to change permissions which seemed to work
would you advise against doing that type of work around?

---

### Post by bodhi.zazen on 2012-05-21
ntfs-3g now support permissions.

Mount the ntfs partition with the permissions option, you can then chown and chmod.

---

### Post by papibe on 2012-05-21
:D Not at all.

Actually, it may be more easy and less intimidating that command line options, so thanks for sharing your solution.

Don't forget to mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Regards.

---

