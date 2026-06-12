---
title: "Signing A File/String/Message (rsa)"
date: 2011-03-07
forum: General Help
---

### Post by shoot2kill on 2011-03-07
Hi, I have had a look around Google, with no luck, I'm hoping someone here can help me better.

I have a String that I would like to sign using a given RSA Private key. I thought this would be relatively easy but I have not been able to find out how to do it, unless I'm looking to far into a simple problem.

Do i have to put the string into a file, and sign the file, or can i just sign the string/message?

any help would be greatly appreciated.. thanks!

-----

String = "Ubuntu"
Private Key File = private.key

---

### Post by Habitual on 2011-03-07
```
man gpg
```

short version:
```
gpg -s <file>
```
"You need a passphrase to unlock the secret key for user:..."
Enter Passphrase:

output on success is file.gpg

ClearSign:
```
gpg --clearsign x
```

"You need a passphrase to unlock the secret key for user:..."
Enter Passphrase:

output on success is file.asc and is ascii content
with this readable output:
```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1


-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.10 (GNU/Linux)

iQIcBAEBAgAGBQJNdRSPAAoJEC+D8KeG8oEFIXUQAJLqw8MGX3E5IWPLAKrNGIMC
EJwzVu2j8Gavmp0Om2IZKdaQywrTA1QdxSc8qudVcbhbRm8Fg91oOPaBGf8VsYA8
7F1umgwZ/kwFAQrcy9srNmCP+QAknK6/XUsq8oPORR8tAEYXUb/03K9zKJTB+k6w
ZbuGJVu0lXoD9UsvJNvri9o5DYM8Gb7kkGzXp85ZwP4pkh2d2zJruLXVdnx3nuYa
UizcvWAorM3Xw9NrivXbBpT4y3N8Ck4OUQ/D5UqAJ9CGYiURTk1HM/DD7d7kq8KA
AJHvnbCWc5aiyDk0asfasfafasfasfA*43DF+IZuRuN/4+iRf3MCsYqtXhXoGo8B
JQvPZtmynXZNQZg5H6jTAOdj8DdwqmKPIBv7FjZbKgxCyPzFsQmoCEnvcNJ/TZuM
hfO1wrfKAUTl9VNDdn8LOVWrb4rFhReEyKJmBMovBIS7zC5DRxVcfbe7PfDzwUDc
ePqre59QK+aCBzPAEUJqi5aRTURuVa7MbuTRtRXpbeIbcDvuIf7vixqEUMSuQ+s3
WrmE+T3knBj+ReURFsEnN/JOq9KuUWurR4Djr2iY2JwSpQk9s0kSeTJAoqOFDmj9
K4qglwGE1zCzpqfMI4MOYDgtiNLGB2HEsBrgDRygCmO1bizMCZK3zye/Lo3DyJpk
XHoFLOh+xhOtp/0bwGTV
=IQlL
-----END PGP SIGNATURE-----
```

I believe you can cache your Passphrase to sign files in succession. 
It is not recommended because it is consider insecure.


You do have a keyring setup already, yes?
You can use seahorse to verify if you do or don't, under "My Personal Keys"

HTH.

---

### Post by shoot2kill on 2011-03-07
I have found this already, but as far as i can see, this will sign the file/string with my personal private key. I want to sign the data with a private key I have in a file in the format of:

```

-----BEGIN RSA PRIVATE KEY----- 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
-----END RSA PRIVATE KEY-----

```

can this be done, or is there a way of importing this private key file to my keyring, and using this key for the signing?

hope this is clear enough, and thanks!

---

### Post by Habitual on 2011-03-07
> **shoot2kill said:**
> ...is there a way of importing this private key file to my keyring, and using this key for the signing?


Do you have the passphrase for this key?

---

### Post by shoot2kill on 2011-03-07
Is it possible that this key has no passphrase?

I was given a CA private key, and asked to sign a message.

I was given no passphrase.

---

### Post by Habitual on 2011-03-07
I am not sure that a CA certificate file can be used to sign anything except a domain's website
I ran into this with a Mac user and had issues with it.

Sorry.

Someone else may have some information that can help, but I don't.

---

### Post by psusi on 2011-03-07
A CA certificate is used for signing an x.509 certificate used commonly for SSL enabled web sites to identify themselves.  You might want to take a look at openssl, which has tools for CA certificate management, as well as the lower level guts you could use to sign arbitrary strings with an arbitrary key.

---

### Post by shoot2kill on 2011-03-15
Solved with openssl

```

openssl rsautl -sign -inkey private.key -in plain.txt -out signed.txt

```

---

