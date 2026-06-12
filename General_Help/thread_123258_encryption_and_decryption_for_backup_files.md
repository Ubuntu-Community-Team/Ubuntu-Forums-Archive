---
title: "encryption and decryption for backup files"
date: 2006-01-29
forum: General Help
---

### Post by sander marechal on 2006-01-29
Hello,

I'm working on creating a decent backup policy for my system. My plan is to rsync all my stuff to my local server each time I shut down my PC. Then, every 24 hours, the server tar's the synced backup, encrypts it and uploades it to my friend's server. So, I'll have two backups: one on my server and an encrypted one on my friend's server.

I don't know what encryption to use to encrypt the tar file. I've looked at GnuPG but it seems useless. In order to decrypt the backup file I would need my private key, but if my system is hosed and I need to back it up from my friends server, I won't have my private key anymore. So, I need some kind of decent encryption that allows me to encrypt/decrypt a file purely based on a passphrase or something similar.

Any ideas?

Thanks!

---

### Post by lnxpwr on 2006-01-29
hi, gnupg isn't that bad ! my files are also encrypted and send to a storage, but I have my keys on a usb-stick, and I can use every system (with gnupg) to encrypt them.
or just try    zip -e      !
greetinx

---

### Post by sander marechal on 2006-01-29
Thanks :)

zip -e looks right for the job (and I can skip the tar stage as well).

---

