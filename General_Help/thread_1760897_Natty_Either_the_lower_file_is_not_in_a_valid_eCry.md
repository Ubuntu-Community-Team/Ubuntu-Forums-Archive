---
title: "Natty: Either the lower file is not in a valid eCryptfs format"
date: 2011-05-17
forum: General Help
---

### Post by coljohnhannibalsmith on 2011-05-17
Hello,

I keep getting the following message in **/var/log/messages**:

```
[COLOR=Blue]May 17 14:20:58 sophie-laptop kernel: [ 9304.149148] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO[/COLOR]
```Can someone tell me what this message means and what to do about it:confused:

My file system was encrypted before the online-upgrade to Natty.  I believe that it still is...

[IMG]http://www.onlinetutorial.it/wp-content/uploads/2008/11/ecryptfs-key-diagram-356.png[/IMG]




[COLOR=Blue]**Thanks Hannibal**[/COLOR]

---

### Post by coljohnhannibalsmith on 2011-05-17
**More Info:**

eCryptfs is a POSIX-compliant enterprise-class stacked cryptographic filesystem
for Linux.

It provides advanced key management and policy features. eCryptfs stores
cryptographic metadata in the header of each file written, so that encrypted
files can be copied between hosts; the file will be decryptable with the proper
key, and there is no need to keep track of any additional information aside
from what is already in the encrypted file itself. Think of eCryptfs as a sort
of "gnupgfs".

eCryptfs is a native Linux filesystem. The kernel module component of eCryptfs
is part of the Linux kernel since 2.6.19.

This package contains the userland utilities.

[COLOR=Blue]***Does this have anything to do with selecting to encrypt the Ubuntu partition during install***[/COLOR]:confused:

Also, can I uninstall it?





**Thanks Hannibal**

---

### Post by coljohnhannibalsmith on 2011-05-21
[COLOR=Blue]***Do I need eCryptfs if I have my Ubuntu partition encrypted or can I remove it???***[/COLOR]




Thanks Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-22
bump

---

### Post by guneza on 2011-10-27
I know you asked this a while back, but no, you cannot remove it if you have an encrypted home directory.

---

