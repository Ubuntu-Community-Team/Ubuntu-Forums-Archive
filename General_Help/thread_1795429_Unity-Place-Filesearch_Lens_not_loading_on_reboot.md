---
title: "Unity-Place-Filesearch Lens not loading on reboot"
date: 2011-07-02
forum: General Help
---

### Post by mikeym on 2011-07-02
Hi,

I've just tried following [this guide]("http://www.ubuntu-corner.com/2011/05/search-all-files-and-folders-with-new-unity-lens-2/") to install the unity-place-filesearch lens to allow unity to index files from my disk as well as previous;y accessed files. I set loaded it using *setsid unity* then added some basic folders to the newly created ~/.filesearch.cfg such as ~/Desktop, ~/Music, ~/Videos etc. removed ~/ and turned down the indexing depth to 2. 

However the Lens works great as long as I've run *setsid unity* manually during the session, but I've I restart it's gone again and I only seem to be able to access files from my recent history. 

Here's a list of running processes immediately after a reboot:

```

$ps -e | grep unity
 5426 ?        00:00:00 unity-window-de
 5454 ?        00:00:00 unity-panel-ser
 5515 ?        00:00:00 unity-applicati
 5517 ?        00:00:00 unity-files-dae
 5519 ?        00:00:00 unity-filesearc

```

And here's one after a *setsid unity*

```

$ ps -e | grep unity
 5426 ?        00:00:00 unity-window-de
 5515 ?        00:00:00 unity-applicati
 5517 ?        00:00:00 unity-files-dae
 5519 ?        00:00:00 unity-filesearc
15635 ?        00:00:00 unity
15659 ?        00:00:00 unity-panel-ser

```

---

### Post by mikeym on 2011-07-03
Sorry, bump.

---

