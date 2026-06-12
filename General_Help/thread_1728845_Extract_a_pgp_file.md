---
title: "Extract a pgp file?"
date: 2011-04-14
forum: General Help
---

### Post by Johnsie on 2011-04-14
Hi how do I extract a pgp file on Ubuntu? I have the file and a passphrase. On Windows I have Kleoptra so I can right click the file and click 'decrypt'. Is there an easy way to do this on Ubuntu?

(a command line method is ok)

---

### Post by TeoBigusGeekus on 2011-04-14
Could [this]("http://www.techrepublic.com/blog/opensource/encrypting-and-decrypting-files-with-gnupg/168") be of any help?

---

### Post by Johnsie on 2011-04-14
Thanks. I have been trying:

> sudo gpg --output file.ext --decrypt file.pgp

But getting the message:

> 
tester@postalhub:~$ sudo gpg --output file.ext --decrypt file.pgp
gpg: AES256 encrypted data
gpg: gpg-agent is not available in this session
gpg: encrypted with 1 passphrase
gpg: decryption failed: bad key


---

### Post by psusi on 2011-04-14
If you weren't prompted for the passphrase then it looks like it was encrypted with a key instead of a simple passphrase, so you will need that private key in your keyring.

---

