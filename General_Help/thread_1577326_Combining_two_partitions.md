---
title: "Combining two partitions"
date: 2010-09-18
forum: General Help
---

### Post by OpressedCalamity on 2010-09-18
Hello, How would I combine a empty partition with my existing partition? A reinstall is just an option and I need more disk space Thanks for anyhelp

---

### Post by quadproc on 2010-09-18
You can probably do what you wish to with the GParted tool.  This tool can be downloaded and installed by using Synaptic if you don't already have the tool.  Edit: this tool also appears to be available from the Software Center; see the Applications menu last item if you are running Ubuntu 10.04.

I think that you could just resize your existing partition and get what you want, if I read your post correctly.

Changing partitions requires a couple of prerequisites: 1. You need to have a complete backup of everything that matters on the disk that you plan to alter, just in case something goes wrong, and 2. You have to do the work while the disk is not in use so you typically would boot from a Live CD or its equivalent.

quadproc

---

### Post by srs5694 on 2010-09-18
To elaborate a bit on quadproc's answer, you should be able to delete the empty partition and then resize your other partition to fill its available space. I wrote a two-part piece on partition resizing for IBM developerWorks recently; you might want to consult it: [Part 1](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html) and [Part 2.](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

Post with more details, such as a screen shot of GParted showing your partitions, if you need more advice.

---

