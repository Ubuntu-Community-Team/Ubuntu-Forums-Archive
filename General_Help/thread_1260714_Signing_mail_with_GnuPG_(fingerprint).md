---
title: "Signing mail with GnuPG (fingerprint)"
date: 2009-09-07
forum: General Help
---

### Post by ngmachado on 2009-09-07
Hello,

I successfully installed GnuPG, created a key for my email address and I want to sign all the mail I send. I just want to SIGN, not encrypt.

So if someone receive a mail from me, he'll have to get my public key. I don't want to use public keyservers cause they are easy targets for spammers. I was thinking about creating a webpage in my website to hold the public key, say mywebsite.com/pgpkey.pub

Every mail I send will appear :

-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

<CONTENT>

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.10 (Darwin)
Comment: mywebsite.com/pgpkey.pub

iQIcBAEBAgAGBQJKpb3uAAoJEFgvzgZmzVlOvqsQAKhCgl1e4oKqYoIPX7iwb/il
=gBLF
-----END PGP SIGNATURE-----

Notice the Comment after the VERSION, indicating where my public key is. 

My question is, where should I put the public key fingerprint so the reader REALLY knows that's my public key?

Thank you.

---

