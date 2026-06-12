---
title: "Automatically sync 2 local folders"
date: 2011-11-07
forum: General Help
---

### Post by brendonsoh on 2011-11-07
Can rsync do this? I assume it could I just want to know the exact terminal command

---

### Post by papibe on 2011-11-07
Hi brendonsoh.

rsync for mirroring directories would be my first suggestion, but since it works one way at a time, you would need one command to push the changes and one to pull them.

To push:
```
rsync -av --delete --update dir1/ dir2/
```
To pull:
```
rsync -av --delete --update dir2/ dir1/
```
If you need perfect two-way synchronization instead of mirroring, I would suggest taking a look at Unison. It is on the Software Center.

Hope that helps,
Regards.

---

### Post by searchfgold6789 on 2011-11-07
To make sure that two directories always have exactly the same contents:```
rsync -a --delete /foo/bar /tic/tac
```Run the command every time you want the folders to be synchronized.

---

### Post by brendonsoh on 2011-11-07
Unison actually ended up being perfect, thank you very much

---

### Post by papibe on 2011-11-07
:D Glad Unison is working for you! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Regards.

---

