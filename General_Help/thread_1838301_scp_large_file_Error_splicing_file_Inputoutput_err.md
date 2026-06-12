---
title: "scp large file: Error splicing file: Input/output error"
date: 2011-09-03
forum: General Help
---

### Post by biggiee on 2011-09-03
I recently set up an SSH server mainly for file transfer, and it works... for the most part. It wasn't until resently when I tried to transfer a large file, once i tried to copy the transfered file to a usb device I recieved the message **Error splicing file: Input/output error**.

Is there a way to verify the file on a local computer to the remote host?

---

### Post by e79 on 2011-09-03
Is this USB device formatted as Fat32, NTFS, ext4 ?

How large is the file you are trying to copy ?

Do you have spaces in the destination folder in your scp commands ?

What if you try with a smaller file on the same destination USB drive ?

---

### Post by biggiee on 2011-09-03
logged into remote box to verify original file and failed. Downloaded file a second time and works fine.
scp not to blame
Thanks for the quick responce e79

---

### Post by e79 on 2011-09-03
My pleasure,

I'm glad you could identify and resolve your issue !

Cheers

---

