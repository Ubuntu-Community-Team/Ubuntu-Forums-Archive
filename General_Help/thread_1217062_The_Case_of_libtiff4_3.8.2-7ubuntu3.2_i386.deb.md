---
title: "The Case of libtiff4_3.8.2-7ubuntu3.2_i386.deb"
date: 2009-07-19
forum: General Help
---

### Post by Infinite Indefinite on 2009-07-19
I ran Update Manager and managed to update everything except libtiff4.

Regarding libtiff4, it seemed that libtiff4_3.8.2-7ubuntu3.2_i386.deb was not available on the repository.

(I tried synaptic as well - same result).

I searched a bit and found that it was indeed not available.  What was available was an updated version - namely 

libtiff4_3.8.2-7ubuntu3.4_i386.deb.

I downloaded and installed that, and checked with update manager again.  It stated that my system was now fully up-to-date.

So in case anyone else has the same problem, I suggest going to:

[http://security.ubuntu.com/ubuntu/pool/main/t/tiff/](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/)

and downloading (if you are using Hardy on a 32bit machine):

libtiff4_3.8.2-7ubuntu3.4_i386.deb

I hope someone will correct the error in the update manager, so that instead of searching for libtiff4_3.8.2-7ubuntu3.2_i386.deb , it searches for libtiff4_3.8.2-7ubuntu3.4_i386.deb instead.

---

### Post by kostkon on 2009-07-19
I think it was not available on the server that your system checks for updates. You can change the server used in *System &#8594; Administration &#8594; Software Sources*.

The thing you then did is to fetch the file from the main Ubuntu server where obviously the updated file exists there just fine.

Thus, I would recommend you to change the server you are using if you believe the current one is giving you problems with corrupted or missing files.

---

### Post by Infinite Indefinite on 2009-07-22
> **kostkon said:**
> I think it was not available on the server that your system checks for updates. You can change the server used in *System &#8594; Administration &#8594; Software Sources*.

The thing you then did is to fetch the file from the main Ubuntu server where obviously the updated file exists there just fine.

Thus, I would recommend you to change the server you are using if you believe the current one is giving you problems with corrupted or missing files.

Thanks - I made the change.

---

