---
title: "Making a password protected archive in linux"
date: 2012-09-28
forum: General Help
---

### Post by CrimpJiggler on 2012-09-28
If you want to make a password protected archive that only you will be accessing, what would be the best way to go about it? I know how to make password protected .rar files in Ubuntu and from what I read, they are pretty secure, the only way to hack them I know of is brute forcing. I notice that in linux, the main type of archive used seem to be .tar.gz files. Can you securely password protect .tar.gz files, similar to how it can be done with .rar files? Are there any advantages to using tarballs? Well, what I'm really asking is what is the best way to create an encrypted archive in linux (in terms of security and practicality)? Are rar archives the way to go or are there better archives? I read somewhere that .7z archives are more secure.

BTW, I know that creating an encrypted partition with truecrypt or other software is the most practical and effective way to protect your files but in some cases (i.e. if its just a handful of text files), its more practical to just keep them on your desktop rather than having to mount an encrypted partition every time you wanna access the files.


EDIT: With rar archives, you can either make it so people can see whats in the archive but need a password to extract the files, or you can make it so they can't even see whats in the archive without a password. The latter is what I'm looking for. To do it with rar files in Ubuntu, you just use this command:

** rar -hp a archive.rar yourfiles**

The p parameter (is that the right word?) is for password protecting the files and the h parameter is to password protect the header too (so you can't view the contents of the archive without a password).

---

### Post by Lars Noodén on 2012-09-28
If you do it with tarballs, then the encryption must be done separately.  You can use [gpg](http://manpages.ubuntu.com/manpages/precise/en/man1/gpg.1.html) (PGP) for that.  It's quite easy, but an extra step nonetheless:

[http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html](http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html)

There is nothing built into tar for encryption.

---

