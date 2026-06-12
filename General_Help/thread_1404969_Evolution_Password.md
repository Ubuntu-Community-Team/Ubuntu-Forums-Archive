---
title: "Evolution Password"
date: 2010-02-12
forum: General Help
---

### Post by brusegadi on 2010-02-12
I read on the evolution FAQ that evolution was storing passwords in .gnome2_private (HOME dir) without encryption.  I got scared, so I went and checked and found nothing in the dir.  Where are the passwords stored now?  Are they plain?  Thanks!  B

---

### Post by Grenage on 2010-02-12
From the FAQ:

 Where does Evolution store my data?
> 
Evolution stores your data in $HOME/.evolution/, your account settings in $HOME/.gconf/apps/evolution and your passwords in $HOME/.gnome2_private/Evolution. The passwords are not stored encrypted, just base64 encoded. SSL Certificates are stored in $HOME/.camel_certs, and if Evolution crashed while you were writing an email, there could even be a file $HOME/.evolution/.evolution-composer.autosave-123456 (where 123456 is some string). Note: If you run Evolution 2.8 or older, the file will be at $HOME/.evolution-composer.autosave-123456.

The newer versions use the Gnome Keyring, with AES encryption.

---

