---
title: "How do I encrypt a single file in Ubuntu 10.04?"
date: 2010-07-05
forum: General Help
---

### Post by mahela007 on 2010-07-05
How do I go about encrypting a file in Ubuntu 10.04?

---

### Post by cj.surrusco on 2010-07-05
You can compress it and then add a password if that's what you want to do. Just right click the file and click compress, choose a compression format, then choose a password.

---

### Post by mahela007 on 2010-07-05
IS there any other way to do it without compression?

---

### Post by bobcollard on 2010-07-05
> **mahela007 said:**
> IS there any other way to do it without compression?
If you are using OpenOffice you can save-as and put it under a password protection.  Another alternative is using an encryption based applet like TrueCrypt, find it here:
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by mahela007 on 2010-07-05
I was doing a little searching on my own.. and it seems odd that seahorse doesn't have a feature to encrypt files.
Truecrypt seems a bit too complicated for my needs.

---

### Post by AlphaLexman on 2010-07-05
I read somewhere, sometime that you can hide ANY file inside a jpeg.
I don't have the link any more, but google would.

---

### Post by mahela007 on 2010-07-05
I've heard of that too but i believe that's a complicated process.... I know I probably sound stubborn but in windows, it's just a question of clicking on properties and selecting "encryped"... 
Would PGP keys be suitable for me? I don't know what they are or how they work but I know that seahorse supports them..

---

### Post by AlphaLexman on 2010-07-05
I know you said you wanted to avoid compressing the file, but 'tar' can simply store the file and you could add a password.

---

### Post by cj.surrusco on 2010-07-05
> **AlphaLexman said:**
> I know you said you wanted to avoid compressing the file, but 'tar' can simply store the file and you could add a password.

.tars don't let you add a password.

---

### Post by mahela007 on 2010-07-06
Oh well.. I'll try compression with passwords.

---

### Post by jbrice on 2010-07-06
Perhaps use KeePassX (it's on the Ubuntu Software Centre) ? 

Start a new KeePass file with your choice of password, add a dummy entry, attach your file to that entry, and save the KeePass file.

---

### Post by mikewhatever on 2010-07-06
Take a look at the link below for single file/folder encryption.
[http://ubuntuforums.org/showthread.php?t=1520469&highlight=encrypt](http://ubuntuforums.org/showthread.php?t=1520469&highlight=encrypt)

---

### Post by mahela007 on 2010-07-07
if I use PGP encryption, wouldn't anyone with access to my public key be able to view the file? The file contains some passwords which I would like to keep er.. secret.
EDIT: There probably are better alternatives to storing passwords.. if anyone know one, please let me know. Meanwhile, I'd like to concentrate on encryption.

---

### Post by bobcollard on 2010-07-07
[http://linux.dipin.info/2009/09/keepassx-password-manager-for-linux.html](http://linux.dipin.info/2009/09/keepassx-password-manager-for-linux.html)
Try KeepassX

---

### Post by mahela007 on 2010-07-08
Ok.. I'll try that.

---

