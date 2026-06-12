---
title: "Seahorse refuses to decrypt file"
date: 2010-01-19
forum: General Help
---

### Post by pveurshout on 2010-01-19
I'm having a major problem with decrypting PGP encrypted files: when using one of my own public keys to encrypt files, they refuse to decrypt. Seahorse asks for the passphrase, I enter it and hit OK, and then it does...nothing. If I encrypt and decrypt files using another of my own public keys it works just fine, and creates a copy of the unencrypted file in the same folder. Anyone have any ideas as to why it stopped liking one of the keysets while having no problems with the other?

EDIT: some additional information: right before noticing this behavior I did have a problem with the key cache refusing to clear this key. I have no idea why, though.

EDIT: it now seems to work again for new files, but there still is a file remaining which just won't get decrypted :???:

---

### Post by pveurshout on 2010-01-19
OK, nevermind. I think I know why it won't decrypt: the original file is empty. Sorry guys.

---

