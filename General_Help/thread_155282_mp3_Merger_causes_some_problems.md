---
title: "mp3 Merger causes some problems"
date: 2006-04-04
forum: General Help
---

### Post by chronusdark on 2006-04-04
i merged some mp3 files using 
```
cat files to merge > output file
```

but now when i play them on my ipod they stop 10 minutes into it but if i skip over the part where it quits it works fine...so im thinking its encountering a premature EOF from the old mp3 file...is there an easy to remove this problem?

---

### Post by LKRaider on 2006-04-04
Hmm, never thought about merging mp3's, but somehow I think cat will mess things up...

From [this blog entry]("http://nion.modprobe.de/blog/archives/444-Merge-mp3-files.html") I found about the [mp3wrap]("http://mp3wrap.sourceforge.net/") project on sourceforge. Try that instead of cat.

---

### Post by chronusdark on 2006-04-04
the problem is i already deleted my originals.....all i have are the merged files... what i need is a program that will let me remove the problematic frames which i believe is the mp3 equivilant to EOF

---

### Post by LKRaider on 2006-04-04
Oh... I don't really know how to clean it up manually...

You could try using [mp3splt]("http://mp3splt.sourceforge.net") to cut the files where you want, and re-join them with mp3wrap, tho I'm not sure how it will work.

Another idea is to try programs that "fix mp3"... tho I only found Win32 solutions, like [Mp3/Tag Studio]("http://www.wma-mp3.com/mp3_tag_studio.html") and [Mp3 Repair Tool]("http://www.snapfiles.com/get/mp3repairtool.html"). You could try running them in wine to see if they fix the file in question.

---

