---
title: "Trash applet 9.10 not emptying"
date: 2010-01-25
forum: General Help
---

### Post by vdings on 2010-01-25
My Trash applet always shows that there are 2 items in the trash can.

Its driving me insane.

I tried sudo rm -fr /home/*/.local/share/Trash to no avail.

Where is the trash folder in karmic? I had to create the Trash folder in home first.

Has it been moved from the /home tree?

---

### Post by LuisGMarine on 2010-01-25
Could be that one of those files is owned by the root users, hence you are a regular user can't delete it.  Read this post and try the commands there and let me know if it gets rid of your problem.

[http://ubuntuforums.org/showpost.php?p=4800640&postcount=3]("http://ubuntuforums.org/showpost.php?p=4800640&postcount=3")

---

### Post by cenzorrll on 2010-01-25
it may be that the files are on a drive you had in earlier that you deleted files from.  ubuntu creates a hidden trash folder on each of the partitions or drives you delete from and puts the files in there from that partition.  i had something like this happen before (back in 8.10 i believe) but i haven't seen something like this lately.

---

### Post by vdings on 2010-02-02
managed to fix the trash applet problem, dont ask me what i did, because i just kept trying to rm the trash folder, and then voila it just worked one time and has continued working fine since then

---

