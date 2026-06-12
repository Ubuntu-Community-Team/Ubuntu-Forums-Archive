---
title: "Encrypting a folder"
date: 2010-06-29
forum: General Help
---

### Post by djmoore85 on 2010-06-29
Hey there yall, I am wanting to encrypt files/folders but can't seem to get it on my own, so I am here for help. I tried truecrypt, but can't install it. I have bcrypt installed, but don't know if it is working or not, I run the command in terminal and then get a bunch of crazy characters but nothing saying it was finished or where the encrypted file is. Any help I can get is greatly appreciated.

---

### Post by mikewhatever on 2010-06-30
To use the builtin option, you need to set up an encryption key. Applications->Accessories->Password and Encryptions,
click File->New->PGPkey and create the key,
when done, you can right click on files and folders and select 'Encrypt'.
If you want to use TrueCrypt instead, specify what was wrong with the installation.

---

### Post by djmoore85 on 2010-06-30
Thank you for the reply. I created a PGP key and have restarted my computer and logged out a couple times, but no encryption option is in the right-click menu. And for TrueCrypt, I haven't dug farther into install just yet until the built-in option is a dead end

---

### Post by mikewhatever on 2010-06-30
Hm, do you have seahorse and seahorse-plugins packages installed?
I think the latter one is not there by default. Try installing it, then logout/login.

---

### Post by djmoore85 on 2010-06-30
I went back and double checked, and yes, seahorse-plugins had to be checked. Got TrueCrypt up and running. Quick question, when I use the built-in encryption I get a copy of the file with a PGP extension, is it safe to delete the original file or will I lose my data?

---

