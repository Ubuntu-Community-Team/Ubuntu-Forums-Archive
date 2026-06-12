---
title: "How to password an archive?"
date: 2010-01-08
forum: General Help
---

### Post by gabe17 on 2010-01-08
Hi! I need to know, how can I make an archive passworded, that means, I will set a password for this archive and nobody can open it without this password. The archive is .tar.bz2.

Thanks.

---

### Post by bapoumba on 2010-01-08
Maybe gpg protect it?
I use seahorse: [http://projects.gnome.org/seahorse/](http://projects.gnome.org/seahorse/)

---

### Post by gabe17 on 2010-01-08
How can I use it? I need to be able to unlock the archive on other PC, if my PC crashes, is it possible?

---

### Post by bapoumba on 2010-01-08
Here are a couple howtos to read (I'm sorry, I'm not on my ubuntu box, I think seahorse has a manual too):
[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)
[http://ubuntu-tutorials.com/2007/08/14/privacy-and-encryption-with-pgp-signing-and-encrypting-email-files/](http://ubuntu-tutorials.com/2007/08/14/privacy-and-encryption-with-pgp-signing-and-encrypting-email-files/)

Seahorse makes it easy to encrypt/decrypt, you'll have the options by right clicking on the file.
One important thing is to keep a safe copy (or two..) of your private and public keys, and not to forget the password you've chosen.

To save/restore the keys:
[http://wiki.openskills.org/OpenSkills/OpenPGP+Key+Backup](http://wiki.openskills.org/OpenSkills/OpenPGP+Key+Backup)
You can restore the keys to another computer (so you'll be able to decrypt your archive there).

---

### Post by kenox on 2010-01-08
Use truecrypt: [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads) 
It works under linux, mac and windows! It has got a simple interface and is easy to create and use!

You pre-alot an amount of space(eg 100mb) called a 'TrueCrypt container', then using truecrypt you can mount this 'TrueCrypt container' as a partition and add or remove files on the fly to this partition.
Thus no need to extract like in password protected zip or rar.
Hidden volumes can be created within the container for added safety.
Entire partitions can also be encrypted.

Copy the 'TrueCrypt container' file anywhere and mount it in that platform and use it! Really portable across platforms but you need to have administrative privilege to mount the partition.

One problem is that the Container cannot be resized. But we can create a larger or smaller container and transfer the data to the new container!

---

