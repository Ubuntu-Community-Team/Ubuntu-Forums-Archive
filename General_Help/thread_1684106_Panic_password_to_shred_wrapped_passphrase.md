---
title: "Panic password to shred wrapped passphrase"
date: 2011-02-08
forum: General Help
---

### Post by J V on 2011-02-08
I considered making my system run the following if an incorrect password is entered 10 times in a row or a specific dead-password is entered.
```
shred /home/.ecryptfs/$USER/.ecryptfs/wrapped-passphrase
```Because ext4 doesn't journal the contents of the file, only the metadata, the file would be shredded and it would be impossible to recover the encrypted home folder even with the password.

Is there a simple way I could make GDM check this or would I have to patch and recompile GDM for something like this to work?

---

### Post by J V on 2011-02-10
Bump: Have to patch kernel?

---

