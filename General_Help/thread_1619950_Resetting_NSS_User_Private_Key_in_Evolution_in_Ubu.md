---
title: "Resetting NSS User Private Key in Evolution in Ubuntu 10.10"
date: 2010-11-12
forum: General Help
---

### Post by bushda on 2010-11-12
Hey folks - I'm trying to reset the password that Evolution prompts you for when working with certs. Specifically, the "Enter the password for 'NSS User Private Key and Certificate Services'" password. 

I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=151336&highlight=nss+user+private+key+and+certificate+services"), but they seem to be out of date. The files cert8.db, key3.db, and secmod.db are not in my ~/.evolution, nor was I able to find any files with those names in any folder referencing evolution in my home folder. 

Can someone tell me how I reset this password in Evolution 2.30.3 in Ubuntu 10.10? No amount of googling has been helpful thus far. 

Thanks!
- Dave

---

### Post by Zburatorul on 2011-03-12
Hey,

Actually I followed the instructions on the link you provided and it worked out just fine. My .evolution folder had all but the "camel-cert.db" file.

I quite Evolution. I made a backup of the files, deleted them, started Evolution again and... strangely it already had all the certificates imported. The same certificates the importing of which two minutes ago was asking for the NNS key password.

EDIT: I just realized that since I recently changed systems, I imported my old Evolution folder into the new system, so I might have files that otherwise shouldn't be here. My experience might not be relevant to a vanilla system.

---

