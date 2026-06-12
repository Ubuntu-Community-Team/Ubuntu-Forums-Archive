---
title: "Encrypt string in DES"
date: 2010-12-14
forum: General Help
---

### Post by mrmime150 on 2010-12-14
I have a very simple question that I've spent the last 2 hours trying to figure out how to do. How do I encrypt a string of text into DES, similar to how you can type: echo 'texthere' | md5sum

---

### Post by andrewc6l on 2010-12-16
The easiest way is to install mcrypt. Note that (unlike md5sum) mcrypt is actual encryption, not just a cryptographic checksum - so you'll have to supply a secret key to encrypt with.

```
$ mcrypt -a des  < plaintext.file > secret.file
Enter the passphrase (maximum of 512 characters)
Please use a combination of upper and lower case letters and numbers.
Enter passphrase:
Enter passphrase:

Stdin was encrypted.
```

Then decrypt with:
```
$ mcrypt -a des -d < secret.file
Enter passphrase:
This is a secret file

Stdin was decrypted.
```

mcrypt also has -a tripledes, which should give you a longer effective key than plain DES. (Although I'm not sure how they generate the key for triple-DES - typically you have two or three keys, but mcrypt seems to pay attention only to the first. It may split the 512-byte key you supply into chunks and use the chunks, since DES has 56-bit keys.)

---

