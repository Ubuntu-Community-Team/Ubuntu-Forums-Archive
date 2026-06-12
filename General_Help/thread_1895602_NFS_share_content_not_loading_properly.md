---
title: "NFS share content not loading properly"
date: 2011-12-15
forum: General Help
---

### Post by Stearns on 2011-12-15
Hi.

To put it simply, I've got a filearchive that runs Ubuntu 10.04 with NFS for sharing its content. Now, since day one I've been having issues accessing the content properly (an issue that's been present regardless of trying to access it through Ubuntu or Windows) as they don't "load" properly. Files and directories tend to show as links rather than what they actually are, and the directory needs to be reloaded for me to be able to view the content properly. This happens pretty much any time I'm trying to access files through e.g XBMC or any music player a lá Clementine, which forces me to open the file-manager Krusader to reload respective directory and then I'll be able to load the files in above mentioned applications. This band-aid method only works once, though, which forces me to repeat it every time I need to switch directories in the applications.

I've been googling around a bit and the only hints to the issue I've come across is that it might be timeouts that's causing this whole mess. It's also worth mentioning that except this, NFS works fine. During transfers I get what speed I should be expecting and the stability is no issue at all, it's just this bit I've detailed above.

---

### Post by Stearns on 2011-12-15
Bumping this as it's causing some major issues for me. Anyone that knows of a possible solution?

---

### Post by Stearns on 2013-02-02
I've been googling this quite a bit and it seems to be a common issue albeit without any proper fix. Anyone that can shed some light on what's going on?

---

### Post by SeijiSensei on 2013-02-02
I just mount the remote share under /media with no_root_squash as an option in the server's /etc/exports.

/etc/exports on server
```

/media/storage  192.168.0.0/16(rw,no_root_squash,async,insecure)

```

/etc/fstab on client
```

server:/media/storage /media/storage nfs defaults,rsize=32768,wsize=32768  0 0

```

I have never had any of the problems you describe, and I've been using this method for years.

---

### Post by Stearns on 2013-02-08
I manually edited the necessary files according to your example and it seems to be working now, oddly enough. Prior to manually editing them, I always used Webmin to export/add NFS mounts with the default settings as I was recommended to do by a friend of mine. He never had any issues following those guidelines which was a bit puzzling, but I guess each case is unique. 

Thanks for the help, I'm glad to finally have the problem solved.

---

