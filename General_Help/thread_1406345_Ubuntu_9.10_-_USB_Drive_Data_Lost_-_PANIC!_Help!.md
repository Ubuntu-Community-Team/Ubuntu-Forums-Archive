---
title: "Ubuntu 9.10 - USB Drive Data Lost - PANIC! Help!"
date: 2010-02-13
forum: General Help
---

### Post by srajama on 2010-02-13
Hi All,

I had some backed up data on a Toshiba External drive and decided to move it my home directory and it looks like I did an cut and paste as opposed to copy paste. I had something like 50 G of data that I wanted moved, and in the middle of the move, it looks like something screwed up. 

Now, there is no data on the external drive (formatted with FAT 32) and my own home directory has a folder by the same name and has only 550 MB! 

Ok - What now? 

PS : Sorry if this is the wrong topic, let me know if I have to move it ...

---

### Post by mechro on 2010-02-13
Try testdisk (available via Synaptic).

If testdisk can read the partition table it might read all your files as "deleted"(highlighted in red). You can then copy and save them.

---

### Post by srajama on 2010-02-13
That was a quick reply! Thanks!

I had Several directories under a directory called and now I can only see a .TMP directory which has some but definitely not all my data. 

I found my music under there, but a "Documents" folder (the one that I really wanted, murphy's law :( ) is still missing... Any suggestions on other tools like scalpel, foremost etc?

---

### Post by srajama on 2010-02-13
Actually yay! I found another .TMP directory which had my data. I'm good for now.

---

