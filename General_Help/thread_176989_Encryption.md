---
title: "Encryption"
date: 2006-05-15
forum: General Help
---

### Post by drpepper on 2006-05-15
Ok, this isnt strickly ubuntu related, but. I need to keep a file wit info secure. TOTALLY Secure. Encryption? Cryptography? i'm nt sure what these are or how to use them. Anyone got any ideas? I have never needed to do anythin like this before so no ideas where to start! Thanks everyone

Nick

---

### Post by mjm115 on 2006-05-15
Have you looked into pgp?

---

### Post by steve.horsley on 2006-05-15
You probably want gpg - gnu privacy guard. It should be installed by default. try **man gpg**. The man page is a real pig to read. If you search synaptic fog gpg, there are several gui fromt ends. I've never tried any.

---

### Post by northface on 2006-05-15
Look here: [http://seahorse.sourceforge.net/](http://seahorse.sourceforge.net/)

1. Add Universe-repository
2. sudo apt-get update
3. sudo apt-get install seahorse

---

### Post by cgjones on 2006-05-15
> TOTALLY Secure

If you can, don't keep the file on a networked computer.

---

### Post by nocturn on 2006-05-16
There is no such thing as totally secure, but you can choose an appropriate level of security for the sensitivity of the file.

If you are really, really concerned, GPG encrypt it, put the GPG keys on a removable medium and keep it on you at all times (except in the shower).

Secure wipe the orignal after encrypting (this does not work fully on journalling filesystems, so use ext2 for this).

Build your computer with an encrypted swap partition to avoid recoverable traces and secure-wipe of encyrpt your /tmp partition.

I'm off course not sure if the file justifies this level of caution.

---

