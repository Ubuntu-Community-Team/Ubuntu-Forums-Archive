---
title: "Disappearing hdd space"
date: 2009-11-12
forum: General Help
---

### Post by 4t0m1c_w07f on 2009-11-12
Hi
I've been doing a lot of downloading with transmission but my root partion keeps filling up.. I've resized the partition twice with an added 30gb of space... My downloads are only supposed to take up 9gb and it's supposed to be on another partition... Any idea about the disappearing space?

---

### Post by whoop on 2009-11-12
Run disk usage analyser, and scan the filesystem
```

baobab

```

---

### Post by 1clue on 2009-11-12
Probably your /tmp directory.

Try this:
```

cd /
sudo du -hs *

```

You will get disk usage of every main folder in your drive.  If something looks out of place to you, dive into that directory and try the same to narrow it all down.

If it's /tmp, then you could run tmpwatch on it to clear it out, or you could mount that directory as tmpfs which would clean it out every time you reboot.

---

### Post by 4t0m1c_w07f on 2009-11-12
> **whoop said:**
> Run disk usage analyser, and scan the filesystem
```

baobab

```

Ok i found the source... log files... namely > kern.log.1 > kern.log > messages.1 > syslog.1 > messages

Is it safe to delete these files? And how do i prevent this in the future?

---

### Post by 1clue on 2009-11-12
Yes, it's safe to delete them, but you should set up logrotate to delete them automatically.  It's typical to keep a week or two of logs, so if something happens you have history to compare things with.

If the logs are growing that large that fast, you should look at what's in there.  There's probably a problem that causes continual entries, and that means you should fix that rather than just delete the files more often.

*Edit:*  Actually, logrotate is already configured because you have the filenames with a .1 on the end.  The files will probably also be deleted after so many days too, so focus more on why the files are large enough for them to be a problem.

---

### Post by whoop on 2009-11-12
> **1clue said:**
> Yes, it's safe to delete them, but you should set up logrotate to delete them automatically.  It's typical to keep a week or two of logs, so if something happens you have history to compare things with.

If the logs are growing that large that fast, you should look at what's in there.  There's probably a problem that causes continual entries, and that means you should fix that rather than just delete the files more often.

*Edit:*  Actually, logrotate is already configured because you have the filenames with a .1 on the end.  The files will probably also be deleted after so many days too, so focus more on why the files are large enough for them to be a problem.

Yep. I for one would like to see those logs or at least part of them, might be something that needs fixing. Looks like something is spamming like crazy :D

---

