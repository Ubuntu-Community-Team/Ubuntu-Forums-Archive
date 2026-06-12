---
title: "When mounting CIFS share, app files are owned by root"
date: 2011-07-26
forum: General Help
---

### Post by rhugga on 2011-07-26
I'm trying to mount some CIFS shares (NetApp) to my Ubuntu 11.04 desktop (64-bit).

I am mounting it as a domain user with admin rights and full control over the share. After mounting it as root, all the files are owned by root and I can't modify them from my non-root user.

Here is how I am mounting the share:

mount -t cifs -o domain=example,username=example-user,password=mypassword //myfiler.example.com/myshare$/mydir    /mnt/myshare/

This share is a qtree under a volume with security type set to NTFS. (Although I have also tried security type = Mixed) We don't configure user-level access to shares on the filer, we create directories and lay down permissions on those from the Windows side. (Although I have tried explicitly adding my domain user to the access list for the share)

My domain user works fine when mounting this from any windows machine as well as from Mac OS X.

---

### Post by Morbius1 on 2011-07-26
It sounds like NetApp is using a UNIX-like implemtation of Samba so to your list of options either take possession of the mounted share by adding:
```
uid=1000
```Or leave the owner as root and change permissions of the mounted files by adding:
```
dir_mode=0777,file_mode=0666
```

---

### Post by rhugga on 2011-07-26
Thx, that did show files and directories with world writable bits and when I open a file within Excel it doesn't show as read-only, however when I try and save changes to gives me a sharing violation error.

Any ideas?

Thx,
CC

---

### Post by Morbius1 on 2011-07-26
I run the risk of you thinking I'm making this up but add yet another option to your list:
```
nobrl
```From man mount.cifs:
                                                      > **nobrl**
           Do not send byte range lock requests to the server. This is
           necessary for certain applications that break with cifs style
           mandatory byte range locks (and most cifs servers do not yet
           support requesting advisory byte range locks).                      

---

### Post by rhugga on 2011-07-26
I added that and same problem.... *pulls hair out*

This is my last obstacle to replacing my windows and mac machines completely.

Do I need to join my ubuntu machine to the Windows domain to get this to work correctly?

---

### Post by Morbius1 on 2011-07-26
The only other option I can think of doesn't seem applicable since you already said your files are 666 but that's:
```
nounix
```Other than that I think I'm out of ideas. Sorry.

---

