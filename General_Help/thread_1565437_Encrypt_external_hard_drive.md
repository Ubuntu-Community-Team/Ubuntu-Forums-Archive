---
title: "Encrypt external hard drive"
date: 2010-08-31
forum: General Help
---

### Post by XAZero on 2010-08-31
Hi all

i think this has not been asked before so here i go..

How do i encrypt an external ext4 hard drive using the same software that is used if you chose to encrypt your /home (at install time)?

i think i heard somewhere that is was truecrypt, so ubuntu (kubuntu i my case) already ships truecrypt doesn't it?

that is because my hard drive is too small and i want all my files in the external hard drive, but i don't want to have all the /home as i'd rather keep the config files on the internal hdd.

Thanks in advance

---

### Post by XAZero on 2010-09-01
bump

---

### Post by katoiam on 2010-09-13
I would also like to know about this!
thanks

---

### Post by DaveHi on 2010-10-02
Hi All

Just saw this and don't know if you have found answer elsewhere, but, in case anyone else comes across this post with the same question have a look at the video below;

[http://www.youtube.com/watch?v=M4JYkZxnhJw](http://www.youtube.com/watch?v=M4JYkZxnhJw)

Please allow me to stress, backup,backup,backup! In fact if your not used to handling volumes and partitions I would suggest you backup _all_ important information on computer before starting.

Stay safe and secure.

---

### Post by walwal on 2010-10-02
yeah its truecrypt but u must download and install the deb file from their site :
truecrypt,com

---

### Post by XAZero on 2010-10-19
so, if truecrypt is what is being used to encrypt the internal hard drive, why is it that you have to install it to use it on other hdd?

---

### Post by killernurd on 2011-03-11
TrueCrypt is third-party, open-source software, but it's *not* the software used for the 'encrypt your home directory' option that Ubuntu ships with.

The software that Ubuntu ships with is called dm-crypt. In the standard install image, dm-crypt can be used to encrypt your home directory, and in the alternate install image can be used with LUKS to encrypt your entire hard drive.

You can use either TrueCrypt or dm-crypt to encrypt your external disk. TrueCrypt has a nice GUI, and is pretty reliable, even if it is a bit on the slow side. It also has a few neat features, some of which were picked up by dm-crypt, like the ability to use a particular file or device as the encryption key for your encrypted volumes. dm-crypt is integrated directly with the Linux kernel, and is both reliable and *fast*. Either option will do what you want to do with it, but here's a page in the Ubuntu community documentation on encrypting external storage:

[https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage](https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage)

---

