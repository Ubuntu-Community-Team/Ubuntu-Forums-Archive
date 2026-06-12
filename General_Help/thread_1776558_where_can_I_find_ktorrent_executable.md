---
title: "where can I find ktorrent executable"
date: 2011-06-06
forum: General Help
---

### Post by rusty_jones on 2011-06-06
where can I find ktorrent executable? I'm trying to download torrent , when i click download there is no entry for: Open with and I can't find the exe

rusty

---

### Post by seawolf167 on 2011-06-06
There won't be any .exe on your computer unless you have it running in Wine. If you do, you can access your wine programs via Applications -> Wine -> Wine Programs

If you are looking for the path to a package in Ubuntu you can locate it with

```
which *programname*
```

By default, you have a program installed called *Transmission* which handles .torrent files. It should be under Applications -> Internet -> Transmission

---

### Post by iclestu on 2011-06-06
> **rusty_jones said:**
> where can I find ktorrent executable? I'm trying to download torrent , when i click download there is no entry for: Open with and I can't find the exe

rusty

/usr/bin/ktorrent

---

### Post by iclestu on 2011-06-06
> **seawolf167 said:**
> By default, you have a program installed called *Transmission* which handles .torrent files. It should be under Applications -> Internet -> Transmission

transmission is only the default with the standard ubuntu install. the OP lists kubuntu in the post's prefix. Ktorrent is the default for kubuntu

---

### Post by seawolf167 on 2011-06-06
> **iclestu said:**
> transmission is only the default with the standard ubuntu install. the OP lists kubuntu in the post's prefix. Ktorrent is the default for kubuntu

Missed that part - thanks for the correction

---

### Post by SeijiSensei on 2011-06-06
> **iclestu said:**
> /usr/bin/ktorrent

More specifically, right-click the torrent file in Firefox, choose Open With, then enter "/usr/bin/ktorrent" in the dialog box that follows.  Click OK, then check the "use always" box in the original dialog.

If you've already downloaded the torrent file, it's likely that just double-clicking its name will start ktorrent.  If not, check System Settings > File Associations, then navigate to Applications > x-bittorent in the left-hand tree.  On my machine with a vanilla 10.10 installation, the only listed application for that "mimetype" is ktorrent.

Note that Firefox maintains its own set of file associations that are independent of those managed by KDE.

---

### Post by rusty_jones on 2011-06-06
thanks to all

Rusty

---

