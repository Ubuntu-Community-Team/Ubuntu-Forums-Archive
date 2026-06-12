---
title: "Error decrypting home diretory. ECRYPTFS"
date: 2011-03-29
forum: General Help
---

### Post by Ralph.B on 2011-03-29
I was in the middle of synchronising some files between my computer and a drive that I have when suddenly a power failure occurred. I went and replaced the troublesome fuse and shortly after, turned my computer back on. 

At first, the system would not boot. But after another try, it booted but I was unable to access my files.

Long story short, my home directory is encrypted. and I need to access it via a live CD. I manage to do everything until it needs to be decrypted.

This part:

ecryptfs-mount-private.

Once I type that in, I get:

ERROR: Encrypted private directory is not setup properly.

There is at least 1 corrupt document or sub-directory in there that I know of. Could this have corrupted the whole home directory? Also, can the encrypted directory be "setup properly"? I appreciate any help regarding this problem.

Thanks in advance.:)

---

### Post by gopherofdoom on 2011-04-09
I had exactly the same problem just now, caused by a memory freeze partway through upgrading to Natty Beta 1...

Finally managed to get this method to work: [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Long%20way](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Long%20way) and I'm now busy copying everything across to my external HDD. Phew.

Hope this works for you if you haven't already sorted it.

---

### Post by Ralph.B on 2011-04-10
Thanks gopherofdoom, that sorted it.

---

