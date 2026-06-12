---
title: "Accessing encrypted home folder"
date: 2010-01-13
forum: General Help
---

### Post by Falc7 on 2010-01-13
I have two kubuntu partitions, both with encrpted HDDs, when i try to access my home folder it says access-your-private-data.desktop. When i root dolphin and try t open this file, it says please enter your passphrase, which dosen't seem to be my root password. So i am unable to open my other home folder, can someone help? I definately didn't set a pasphrase before

---

### Post by Falc7 on 2010-01-13
I've tried this:
> Recovering Your Mount Passphrase
In the event that you did not write down your mount passphrase, you may be able to recover it by decrypting the file  ~/.ecryptfs/wrapped-passphrase  using your login passphrase.

 ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase "login passphrase" 
It's a good idea to clear your shell history at this point to erase your login passphrase
 history -c 
If your login passphrase matches the passphrase used to encrypt the wrapped-passphrase file, your mount passphrase will be written to screen. Record and protect this data accordingly.

If you have lost your wrapped-passphrase file, and you did not record your mount passphrase, it is impossible to access your encrypted data.

from here: [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering) Your Mount Passphrase

Following that it gives me a passphrase, but then it says passphrase incorrect when i try to open the home folder.

---

