---
title: "FTP rejecting all operations"
date: 2012-02-28
forum: General Help
---

### Post by JackTheKnife on 2012-02-28
I have running Ubuntu 10.04 and after latest update any FTP operation from PC to Ubuntu machine is rejecting (copy/create file, copy/create folder, etc).

Any clue what is going on?

Thanks

FYI

I'm using WinSCP

---

### Post by JackTheKnife on 2012-02-28
OK, found issue - /home run out of space. Strange - need to check why.

---

### Post by gsgleason on 2012-02-28
du -sh /home/*

---

