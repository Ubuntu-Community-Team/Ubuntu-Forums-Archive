---
title: "Disk boot failure insert system disk and press enter while first boot.."
date: 2010-08-18
forum: General Help
---

### Post by Sf3d0 on 2010-08-18
I'm trying to do exactly this: [http://www.youtube.com/watch?v=Fy1ISEJIv84](http://www.youtube.com/watch?v=Fy1ISEJIv84)
the first time i did it, i made it and everything was fine, except i didn't know what "installation size" meant in wubi, so as i selected 3GB, the rest of the partition was left empty and I didn't have enough space for ubuntu..then i formatted the partition again and reinstalled ubuntu..since then while it's booting, i get the message Disk boot failure insert system disk and press enter..tried reinstalling many times, but i still get this message..

---

### Post by Sf3d0 on 2010-08-18
up..? ):P

---

### Post by Sf3d0 on 2010-08-18
anyone..?

---

### Post by jimbop99 on 2010-08-18
I'm a little confused. You installed ubuntu using wubi and made the partition to small. The part I don't quite understand is you "formatted the partition". For a wubi install all you need to do is uninstall via windows and reinstall making the partition larger the next time. If you actually "formatted" your wiped out you entire windows install.

---

### Post by Sf3d0 on 2010-08-18
> For a wubi install all you need to do is uninstall via windows and reinstall making the partition larger the next time. If you actually "formatted" your wiped out you entire windows install.

If you saw the video, the guy makes a second partition, where he chooses ubuntu to be installed..thus (Via windows) you can actually format every single partition that you made on your hard disk, without formatting the entire disk..;) i didn't uninstall and reinstall, because there is an error every time, so I format the partition and make a new volume every time..

---

### Post by jimbop99 on 2010-08-18
I attempted to watch the video but couldn't get it to full screen so I wasn't sure what was going on. I now understand what your trying to do. So if I'm understanding you correctly, you can't get into windows or Ubuntu? IF so, it sounds like the windows MBR is gone/corrupt.

---

### Post by bcbc on 2010-08-18
> **Sf3d0 said:**
> If you saw the video, the guy makes a second partition, where he chooses ubuntu to be installed..thus (Via windows) you can actually format every single partition that you made on your hard disk, without formatting the entire disk..;) i didn't uninstall and reinstall, because there is an error every time, so I format the partition and make a new volume every time..

So there is a whole lot of stuff that is installed along with the files on that partition you formatted. E.g. the wubildr file, the entries in the registry, the Add/Remove programs entry, etc. etc. While it might have seemed a good idea to simply format the partition, it was actually a bad idea.
When you run wubi.exe, it first checks for an existing install and removes it completely, then it starts the new install. So, that's where it is failing.

I suggest you try to remove ubuntu manually using the instructions [here]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?").

---

