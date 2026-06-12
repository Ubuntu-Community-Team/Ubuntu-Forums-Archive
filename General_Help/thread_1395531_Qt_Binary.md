---
title: "Qt Binary"
date: 2010-02-01
forum: General Help
---

### Post by godmen2 on 2010-02-01
I have downloaded the binary file for installing Qt. It is too large to be saved on my primary ssd of 4 gb sso i saved it on my secondary ssd of 16 gb.

How do i install Qt given these issues. The file is qt-sdk-linux-x86-opensource-2010.01.bin.

Please help.

Thanks,

Harold

---

### Post by raktarok on 2010-02-01
Open a terminal and navigate to the folder where you have the .bin file.
Then do this:
./qt-sdk-linux-x86-opensource-2010.01.bin
It should work.

Or try settng the file as execuatable from the right click properties menu, and executing it from the nautilus itself.

---

### Post by raktarok on 2010-02-01
Sorry, I think I misunderstood your question. Try and see where the .bin file tries to install the files, and then make symbolic links in those places, pointing to the other partition. That should do the trick.

---

