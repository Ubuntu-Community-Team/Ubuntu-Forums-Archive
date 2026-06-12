---
title: "gpg reports decryption failed: bad key"
date: 2009-07-10
forum: General Help
---

### Post by avam323 on 2009-07-10
I have a document which contains very sensitive personal info; i encrypted it using gpg and a password i *know* i am typing correctly. i have other files encrypted in the same manner, using the same passphrase. however, this one file out of the bunch will not open. in attempting to open the file using the command line i get:
```

user@HOST:/path/to/Documents$ gpg passwords.gpg 
gpg: CAST5 encrypted data
gpg: encrypted with 1 passphrase
gpg: decryption failed: bad key

```

the other files open just fine and are NOT really important info, but this one is. i need to open it and soon; thank you in advance for your help.

---

### Post by avam323 on 2009-07-10
let me clarify a few things: i am running jaunty and have rebooted and tried again, with no change. also, i was able to open the file less than 24 hours ago, with no updates to the system since. i have also tried encrypting/decrypting other files using both gnome and the command line, which work fine. how is it possible that this one file got corrupted?

---

