---
title: "File Compare Utility"
date: 2009-09-30
forum: General Help
---

### Post by cabellotl on 2009-09-30
Hi, i'm a new user in the ubuntu world and i have a question, what software can i use in my computer to compare files, in windows there is a FCU (file compare utility) but i cant find it for ubuntu, does someone knows any software?

Thanks

---

### Post by cariboo on 2009-09-30
Open an Applications-->Accessories-->Terminal and type:

```
fc file1 file2
```

for more info type:

```
man fc
```

If you need a gui app, go to System-->Administration-->Synaptic Package Manager and click the Search button and enter:

```
file compare
```

---

### Post by kellemes on 2009-09-30
gui app:
```
sudo apt-get install [meld]("http://meld.sourceforge.net/")
```

---

### Post by dhughes on 2009-09-30
Yes Meld is great and graphical, good if you're new to Linux and not great with the command, prevents confusion too. You can compare three different files and even three directories.

 Watch your settings, I believe directory comparison is not the default so if you find you can't compare it's probably because you didn't choose the directory compare tab.

---

### Post by jkysam on 2009-09-30
You could also try Kompare.

---

