---
title: "encrypt a FILE before sending to cloud"
date: 2011-09-22
forum: General Help
---

### Post by DouglasAdams on 2011-09-22
i backup my personal data, plus some setting/params, using Back in Time.  periodically, weekly'ish, i take the latest backup and create a tar / lzma file with it which i would like to upload to the cloud for backup purposes.  i used to use 7zip but that started to error a while ago, it think the error is something to do with some links i have.  7zip allowed me to password protect my data.  the other options, which give compression similar to 7zip, don't offer encryption, hence, i need another package.
i've tried using truecrypt but the way it works, the sort of "box" idea, is not for me.

ideally i would like to "define" my Ubuntu One directory so that any file placed there gets encrypted automatically.
second choice would be that i create my backup compression file, encrypt it then place the encrypted file in my Ubuntu One dir.

any suggestions please?

---

### Post by searchfgold6789 on 2011-09-22
TrueCrypt would still work, for this. It enables you to automatically mount a truecrypt directory **at startup**, meaning: a box appears, you enter the key, and bam! instantly you have encryption. 
Or you could check out the following projects:
[http://sourceforge.net/projects/kgbarchiver/](http://sourceforge.net/projects/kgbarchiver/)
_[http://www.peazip.org/peazip-linux.html](http://www.peazip.org/peazip-linux.html)_

---

### Post by dethorpe on 2011-09-22
Haven't used Ubuntu one but i'd imagine you could use an EncFS encrypted folder as your ubuntu one folder. 
 
This is easily manage using cryptkeeper to create and mount the encrypted folder, or can do through command line. The encrypted folder could then be set as the Ubuntu One folder.
 
Some isntructions for doing this with dropbox are here [http://www.webupd8.org/2011/06/encrypt-your-private-dropbox-data-with.html](http://www.webupd8.org/2011/06/encrypt-your-private-dropbox-data-with.html)
 
Haven't tried it but should be similer for Ubuntu one if it just uses a folder to sync.

---

### Post by agillator on 2011-09-22
If you are willing to manually encrypt/decrypt, although I realize that is not what you really want, why not use GNUPG?  Encrypt the tarred file with gpg, send it to the cloud. Later if you need it you can easily retrieve it and decrypt it. You can keep your keys on a USB stick so they don't get lost during a drive failure or something. GPG is quick and simple.

---

### Post by DouglasAdams on 2011-09-23
> **searchfgold6789 said:**
> TrueCrypt would still work, for this. It enables you to automatically mount a truecrypt directory **at startup**, meaning: a box appears, you enter the key, and bam! instantly you have encryption._[]("http://www.peazip.org/peazip-linux.html")_
i tried truecrypt, i could not see any option to handle a directory.
yes, you can (as the blurb goes):  create a **virtual encrypted disk** within a file and mounts            it as a real disk.
problem is, when you do that it allocates all the space up-front, you even need to tell it the size of the "box" that you intend to put your files in.

sorry, but that's no good for me - my backups can vary in size, also, Ubuntu One & Dropbox have a max capacity.

thanks for the other links ...

---

### Post by HermanAB on 2011-09-23
Here you go:
Right click, compress, zip, other options, password

---

### Post by Habitual on 2011-09-23
> **HermanAB said:**
> Here you go:
Right click, compress, zip, other options, password

+1 (K.I.S.S. Method)

---

### Post by DouglasAdams on 2011-09-24
> **HermanAB said:**
> Here you go:
Right click, compress, zip, other options, password
i stop using zip for encryption when i saw some zip password hack progs.
has this issue now been resolved?

---

