---
title: "Running a .sh"
date: 2010-07-22
forum: General Help
---

### Post by xpowerfulxx on 2010-07-22
I am trying to run a .sh in Terminal, but even if I run it as root it says Permission Denied.

---

### Post by Nytram on 2010-07-22
It may not have execute permission, try:

**chmod +x filename.sh**

---

### Post by Vaphell on 2010-07-22
or you can run it with **sh filename.sh** - you pass it as a parameter to sh to execute

---

### Post by xpowerfulxx on 2010-07-22
> **Vaphell said:**
> or you can run it with **sh filename.sh** - you pass it as a parameter to sh to execute
Thank you; I tried it and it worked!

---

### Post by Iowan on 2010-07-22
Is it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?  :)

---

