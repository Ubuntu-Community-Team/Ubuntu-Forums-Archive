---
title: "Please some one help me about confirming openpgp."
date: 2012-07-13
forum: General Help
---

### Post by prismctg on 2012-07-13
I dont understand how to confirm lauchpad openpgp key ; i found mail from launchpad ;but now i dont know how to validate this key. I also found validation using "enigmail" ; but its not clear to  me.

---

### Post by MG&amp;TL on 2012-07-13
Copy the text between

```
-----BEGIN PGP MESSAGE-----
```and ```
-----END PGP MESSAGE-----
```**including** those lines.

Then save it in a file. Say you save it in Documents/gpg.txt.

Then run this command:

```
gpg --decrypt ~/Documents/gpg.txt
```to decrypt the text with your gpg key. If all goes well, you should have some readable instructions. :)

---

### Post by prismctg on 2012-07-13
:( ```
gpg --decrypt /home/prism/m.txt
gpg: directory `/home/prism/.gnupg' created
gpg: new configuration file `/home/prism/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/prism/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/prism/.gnupg/secring.gpg' created
gpg: keyring `/home/prism/.gnupg/pubring.gpg' created
gpg: no valid OpenPGP data found.
gpg: decrypt_message failed: eof
```

---

### Post by MG&amp;TL on 2012-07-13
Two questions:

1) On that account, have you got a private key?

2) Can you post what the file looks like? Obviously post garbage rather than the actual data.

---

### Post by prismctg on 2012-07-13
No there is not any private key

---

### Post by Krytarik on 2012-07-13
> **prismctg said:**
> No there is not any private key
Here is an excellent guide on how to create a PGP key and import it to Launchpad:

[http://askubuntu.com/questions/100281/how-do-i-make-a-pgp-key](http://askubuntu.com/questions/100281/how-do-i-make-a-pgp-key)

Regards.

---

### Post by MG&amp;TL on 2012-07-13
> **prismctg said:**
> No there is not any private key

You must have had one to make the key? You can just copy the ~/.gnupg across from that acount/machine.

---

