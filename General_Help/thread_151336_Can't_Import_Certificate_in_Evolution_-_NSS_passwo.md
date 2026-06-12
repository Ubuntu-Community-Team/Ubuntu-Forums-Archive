---
title: "Can't Import Certificate in Evolution - NSS password ??"
date: 2006-03-27
forum: General Help
---

### Post by tazzz on 2006-03-27
Ive searched and asked everywhere for a few months now and NO ONE was able to help me so far !! :(

I used to be able to entre thawte certificate in evolution, but since a few months this is not possible anymore:

everytime i try to import a certificate it asks for:

"Enter the password for `NSS User Private Key and Certificate Services'"

I Have no idea what that is, other that it seems to be an authentification method.. ! I dont have that user, i tried all my passwords ..
I have a root account and that password doesnt work either. Neither does the certificate password etc ..

when i start it from the command line i get this error:
"PK11_Authenticate failed" 
(auth function .. ?)

Can anyone help with this plse !!
I dont like the mozilla interface that much for mail, and I dont want to setup a Windows computer just for Outlook !!

---

### Post by dcstar on 2006-03-28
[QUOTE=tazzz]Ive searched and asked everywhere for a few months now and NO ONE was able to help me so far !! :(

I used to be able to enter thawte certificate in evolution, but since a few months this is not possible anymore:

everytime i try to import a certificate it asks for:

"Enter the password for `NSS User Private Key and Certificate Services'"
......[/QUOTE]
I can only suggest renaming the hidden .evolution directory in your home drive and allow Evolution to create a fresh profile, then see if things work again.

If they do, you should be able to copy your messages etc. across from the old directory.

---

### Post by Eladon on 2007-05-06
I ran into this issue today.  It seems as though Evolution's security config is broken.

I went into my ~/.evolution folder and found these files:
camel-cert.db, cert8.db, key3.db, secmod.db
I have no idea what each of these files are for, but I backed them all up and then deleted all four files.  When I started Evolution again, it automatically recreated all the files except for camel-cert.db

After that, I was able to import the certificate without problems...

---

