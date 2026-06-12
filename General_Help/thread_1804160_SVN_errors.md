---
title: "SVN errors"
date: 2011-07-14
forum: General Help
---

### Post by nathanv221 on 2011-07-14
i have encountered the following error,

taylor@ubuntu:~/Projects/Slicer4/Applications/CLI/Multiply/Data$ mkdir Baseline
taylor@ubuntu:~/Projects/Slicer4/Applications/CLI/Multiply/Data$ svn mv ~/Projects/Slicer4/Testing/Data/Baseline/CLI/MultiplyTest.nrrd Baseline
svn: 'Baseline' is not a working copy

im simply trying to move a file (MultiplyTest.nrrd) into a new directory (Baseline) in order to make the program (Slicer4) more organized. i googled my error and found a few like it but they all involved installing SVN so none of the solutions apply to me. and i have tried deleting Baseline and remaking it. any ideas?

---

### Post by Azdour on 2011-07-14
Hi,

It's probably because you have not added the directory to SVN before doing the svn based move?

---

### Post by nathanv221 on 2011-07-14
i tried adding it to svn and got another error

svn add ~/Projects/Slicer4/Applications/CLI/Multiply/Data/Baseline
svn: '/home/taylor/Projects/Slicer4/Applications/CLI/Multiply/Data' is not a working copy

---

### Post by Azdour on 2011-07-14
Hi,

How much of the new directory structure have you added to SVN? It looks like Data is not added either.

If I am not mistaken you can only use svn mv to move a svn file to a directory that is already part of svn.

---

### Post by nathanv221 on 2011-07-14
thank you. it's now working perfectly!

---

### Post by Azdour on 2011-07-14
Hi,

If you could mark this thread as solved that would be great.

---

