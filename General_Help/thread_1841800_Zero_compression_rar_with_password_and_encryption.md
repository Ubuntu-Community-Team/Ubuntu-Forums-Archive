---
title: "Zero compression rar with password and encryption"
date: 2011-09-10
forum: General Help
---

### Post by notoriousxxx123 on 2011-09-10
How can I 'zero compress' (store-mode .rar) a folder with password protection with encrypted file data and headers in ubuntu?

---

### Post by zero2xiii on 2011-09-10
Right Click on the file/folder, and select compress.

---

### Post by Enigmapond on 2011-09-10
You mean you want to rar without compression?...this is the nature of rar'ing. maybe you should look into TrueCrypt. This will create an encrypted container to store files and doesn't compress them. Seems a bit more practical.

---

### Post by notoriousxxx123 on 2011-09-18
I dont want to encrypt my whole drive. Just a few folders. 

I have to access those only sometimes. I want zero compression because it is faster. (because the data I have to secure is around 5 GB's)

The idea is that whenever I have to access that data I can extract and delete them after use. Keeping that password protected/encrypted (rar) keeps my files secured.

There is option to password protect and encrypt file header in  'archive manager'
but there is no option to choose 'no-compression mode(zero compression)'.
With standard settings it takes a lot of time to compress/decompress.

In my case I just need to avoid unauthorised access to my files and I'm not interested in saving disk space with compression.

> **Enigmapond said:**
> You mean you want to rar without  compression?...this is the nature of rar'ing. maybe you should look into  TrueCrypt. This will create an encrypted container to store files and  doesn't compress them. Seems a bit more practical.

Will that ensure that the files are hidden when windows is running as those folders are located in windows partition (i dont have much free space in ubuntu partition)

I have dual boot with win7. I want to be able to access these files in both windows and ubuntu.

---

### Post by otaniyul on 2012-07-30
you could use command line

```
rar a -m0 -hp -r output.rar folder
```

"-m0" is with zero compression, "-hp" is with password. the problem is that this command is not working for me, it just takes 1 file of the folder.

---

