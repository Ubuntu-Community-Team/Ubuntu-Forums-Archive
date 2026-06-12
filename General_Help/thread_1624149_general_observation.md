---
title: "general observation"
date: 2010-11-17
forum: General Help
---

### Post by rebeltaz on 2010-11-17
This isn't really a request for help, just an observation on Ubuntu (and maybe Linux, I don't know) in general...

Why is the 'random' (I think it's set for so many times of starting Ubuntu up, but it just seems random) file system check run at the beginning of the session? I know Windoze does it that way as well, but that's no reason to perpetuate a wrong. 

It seems to me that running it at the end of a session would make more sense. I don't know about others, but when I power my computer up, I need to use it then. Having to wait the length of time that it takes for the check to complete just seems like an unnecessary inconvenience. I know that I can cancel it (and I usually do) but then I have the same issue the next time I run the system. If the check was run at the end of the session, you could just close the session out and walk away while the system goes about it's business. 

That's just my two cents...

---

### Post by SeijiSensei on 2010-11-17
If the file system has errors and I let you mount it anyway, the errors can propagate, and the file system will become more corrupt.

The reason it happens when the file system is mounted is because, as you surmised, there's a record in the filesystem which keeps track of the number of mounts and length of elapsed time since the last check.  Hitting one of these limits while mounting starts the checking process so it has to happen then.

---

### Post by CharlesA on 2010-11-17
fsck runs after 20 mounts by default. So, reboot 20 times and it'll run a fsck.

---

### Post by rebeltaz on 2010-11-17
> **SeijiSensei said:**
> If the file system has errors and I let you mount it anyway, the errors can propagate, and the file system will become more corrupt.


I understand that, but if you run the test at the end of the session and then the system shuts down, why would there be any errors when you boot back up?

---

