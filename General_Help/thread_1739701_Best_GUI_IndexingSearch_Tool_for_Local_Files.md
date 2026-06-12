---
title: "Best GUI Indexing/Search Tool for Local Files?"
date: 2011-04-26
forum: General Help
---

### Post by LaneLester on 2011-04-26
While working on a document in Ubuntu, my computer froze, requiring a power cycle to regain control. I discovered, upon rebooting, that the partition on my #2 drive where I store documents was no longer accessible.

Many hours later, I had used **photorec** to retrieve the files and store them in a separate partition. Some 130,000 files were now in 265 directories.

The problem is that, while the file extensions are correct, the filenames are cryptic, e.g., f1255160.txt, and I need a tool to identify the contents of the files.

**Google Desktop** is one solution, and I have it currently indexing the retrieval partition. A drawback of this program is you can't search just for certain file extensions.

Is there a Linux program for X that will index the contents of files for retrieval by search?

Lane

---

### Post by dragonfly41 on 2011-04-26
You could try [http://neon.niederlandistik.fu-berlin.de/en/textstat/](http://neon.niederlandistik.fu-berlin.de/en/textstat/)

download python version .. you will need to install python-tk package

e.g. if unzipping to Desktop ..

chmod +x ~/Desktop/TextSTAT2/TextSTAT.pyw
~/Desktop/TextSTAT2/TextSTAT.pyw

then build a corpus of all or chunks of your *.txt files

---

### Post by LaneLester on 2011-04-26
> **dragonfly41 said:**
> You could try [http://neon.niederlandistik.fu-berlin.de/en/textstat/](http://neon.niederlandistik.fu-berlin.de/en/textstat/)

Yes, that looks like just the thing! Thank you.

Lane

---

