---
title: "Text File Become executable once created"
date: 2010-06-03
forum: General Help
---

### Post by tyliew333 on 2010-06-03
Hi, I'm facing a weirld problem, that is when I create a new text file in my pendrive, it become executable automatically. The text file name append with asterisk(*). However when I create a text file in Desktop, the created text file is normal and is not executable.

Another thing is when I copy a PDF file to my pendrive, it become executable file with asterisk (*) append after the PDF name. I've try copy whatever to pendrive but all end up with executable file.

Is that any way to fix the problem? Hope you all can help me.

ty6

---

### Post by Anthon on 2010-06-03
This probably depends on the fileysystem that is on your pendrive and/or how this is mounted.
Can you give the output of
  mount -a | fgrep <pendrivename>

---

### Post by tyliew333 on 2010-06-03
My Pendrive's name is VECAD-TY6.
When I follow your instruction, mount -a | fgrep VECAD-TY6, it could run but gives no outputs.

---

### Post by efflandt on 2010-06-03
USB flash by default is typically FAT or FAT32, which is totally insecure and has no concept of many file permissions.  So if you copy a file to your pen drive, and then copy it back to Linux, it will end up with 755 permissions (-rwxr-xr-x).

So if you copy such files to Linux, you may want to note to use **chmod -x filename** on them or a wildcard of their file extension (*.ext).

---

### Post by tyliew333 on 2010-06-03
Ya, that's true. Whenever I copy a file from pendrive to Linux system the permission change to 755. The same case happen to my hard drive partition as well, whenever I create a new file (even a simple.txt) would set the permission to 777 (-rwxrwxrwx). This is very irritating!!!! 

How can this be solved?

---

### Post by JoelOl75 on 2010-06-03
I think the only way would be to format the usb stick to ext2.  This means it won't be easily accessible in Windows machines though.

Don't use a journaled filesystem (ext3,4) on small drives as it's just a waste of space.

---

### Post by tyliew333 on 2010-06-03
Yeah, I've thinking of formatting the partition to ext3 or ext4. But I want that partition to be accessible by both OS (Linux and windows), I have to format the partition in NTFS. 

Anyway, thanks you so much.

---

