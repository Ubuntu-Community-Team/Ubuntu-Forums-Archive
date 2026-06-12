---
title: "How can I find the repository entry for this?"
date: 2009-09-08
forum: General Help
---

### Post by madu on 2009-09-08
Hey guys...

I really want to install Okular in my SmartQ7 PMP.
The default repository does not have it but this one does [http://packages.debian.org/lenny/arm/graphics/okular](http://packages.debian.org/lenny/arm/graphics/okular)

Could someone please please let me know how to put the repository entry in sources.list? all my effort has been unfruitful.

Cheers.

---

### Post by credobyte on 2009-09-08
```
deb http://ftp.de.debian.org/debian lenny main 

```or

```
http://ftp.de.debian.org/debian/pool/main/o/okular/okular_0.7-2_arm.deb
```[COLOR=Gray]** direct .deb download[/COLOR]

---

### Post by madu on 2009-09-08
> **credobyte said:**
> ```
deb http://ftp.de.debian.org/debian lenny main 

```or

```
http://ftp.de.debian.org/debian/pool/main/o/okular/okular_0.7-2_arm.deb
```[COLOR=Gray]** direct .deb download[/COLOR]

Thank you very much credobyte!
It worked perfectly until it gave a public key not found error right at the end. 
I also did apt-get install debian-keyring earlier.
When I try to export the key I get "gpg: no valid openPGP data found".
Is there anyway I can bypass this key check?

Any help is greatly appreciated.

Thank you again.

---

