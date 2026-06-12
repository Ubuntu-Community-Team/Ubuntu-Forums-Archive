---
title: "Mount FTP directories to local fs - curlftpfs"
date: 2010-08-28
forum: General Help
---

### Post by guandalino on 2010-08-28
Hello! I'm looking for a way to mount remote ftp directories to local filesystem in order to interact with them as if were local resources. I found several tutorials that recommend curlftpfs, but this project seems no longer maintained (last update on sourceforge goes back to Apr 2007).

So, is curlftpfs still the best choice or is there something newer which I could rely on?

Thanks,
best regards.

---

### Post by lmarmisa on 2010-08-28
Try Places -> Connect to server... Service type: FTP (with login) or Public FTP

---

### Post by guandalino on 2010-08-28
Thank you very much, works like a charm! Any way to do the same via command line?

---

### Post by lmarmisa on 2010-08-28
First of all, install the package curlftpfs:

> 
sudo apt-get install curlftpfs
Create the mounting point directory. For example:

> 
mkdir ~/ftpdir
If you wish to mount the ftp server  type this command:

> 
sudo curlftpfs -o allow_other youruser[:yourpassword]@ftp.site.com ~/ftpdir
Finally, if you wish to unmount the directory type

> 
sudo umount ~/ftpdir


---

### Post by guandalino on 2010-08-28
Best support here, thanks again!

Finally I managed this adding a line to ~/.netrc:

```

machine ftp.myhosting.com login myusername password mypassword

```and calling curlftpfs with:

```

sudo curlftpfs -o allow_other ftp.myhosting.com ~/ftpdir

```Another question, will the password pass unencrypted? If so, any way to secure the transmission?

---

### Post by lmarmisa on 2010-08-28
Type this command :D:

> 
man curlftpfs


---

### Post by camelseller on 2013-03-08
Does anyone know how to export a curlftpfs-mounted-folder via nfs or cifs?
I created a folder as a normal user ```
p2p:users
```.
I mounted it using the command:```
curlftpfs -o allow_other ftp://217.147.232.18/pub/ /media/ftp/
```
and then I noticed that the /media/ftp/ folder, become ```
root:root 
``` owned.
Then if I try to export /media/ftp/ I get always [access denied] from the server.

What am I doing wrong?

---

### Post by wildmanne39 on 2013-03-08
Old thread closed! Please start a new thread you can link to this one if you need too.
Thanks

---

