---
title: "Decrypting axcrypt encrytped files in Ubuntu"
date: 2011-09-03
forum: General Help
---

### Post by ledererster on 2011-09-03
Hi all.

After dual booting Windows 7 and Ubuntu for ages, I finally decided to make the switch and just use Ubuntu 11.04.  But I realized that in my backups I had some encrypted files that I used axcrypt to encrypt that I need. I've seen that axcrypt is a windows only app and I was wondering if there's any way I can decrypt them with ubuntu?
I know that pass phrase I used, so i don't need to crack it. I just have no idea how I would go about decrypting my files.

Also, provided I end up getting this to work, does anyone know of a good file encryption program that will run in ubuntu?

Thanks Alot!!

---

### Post by ragtag on 2011-09-03
It as apparently possible to run AxCrypt under Wine, though it's apparently not completely straight forward. Alternately, you could install Windows in VirtualBox, and decrypt your files there, before re-encrypting them again on the Linux side.

As for encryption solutions for Linux there are quite a few options. Ubuntu can do whole disk encryption, but you need to do that as you install the system, which you probably don't want to redo. 

Alternately, individual users home folders can be set to be encrypted. This is a really easy way, and only requires you to log in to access the files. You home folder is stored as an encrypted disk image (single file).

The solution that is most similar to AxCrypt, is probably EncFS and Cryptkeeper (just install Cryptkeeper from the Software Center. It encrypts folder, but still keeps the files as individual files using seemingly random names, rather than a as one disk image. When you mount the folder, you get access to the files. This is quite handy if you're using things like Ubuntu One, SpiderOak or Dropbox to backup your files, as it will still work with the encrypted files.

Then there is TrueCrypt. This is actually a crossplatform program, and creates an encrypted disk image. It can create disk images that are readable by Windows too.

---

