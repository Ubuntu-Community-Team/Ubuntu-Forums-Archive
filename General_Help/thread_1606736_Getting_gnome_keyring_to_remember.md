---
title: "Getting gnome_keyring to remember"
date: 2010-10-26
forum: General Help
---

### Post by tgies on 2010-10-26
Hi,

I'm running UNR 10.10. I have gnome-keyring-daemon loading on startup and the PAM modules unlocking my keyring with my password when I log in. ssh-add finds my SSH key in .ssh and loads it. It also appears on the "Private Keys" tab of seahorse. Great!

Right now, the first time I log into SSH every session, a gnome-keyring-prompt comes up asking for the passphrase to my private key:

> Enter password to unlock the private key.

An application wants access to the private key 'id_rsa', but it is locked.This passphrase is then cached on my keyring for the duration of the session (i.e. until I log out).

What I would like to do, and what I know I used to be able to do around 8.04, is cache the passphrase on the keyring *forever.* It seems to me that there used to be an "Automatically unlock" checkbox on the gnome-keyring-prompt dialog that would store the passphrase in the encrypted keyring and use it to decrypt the key automatically when the keyring itself is decrypted. I don't see this option anywhere anymore. Where did it go and how can I get this behavior back?

---

### Post by tgies on 2010-10-27
Would a mod mind fixing my thread title? It ought to be **Getting gnome_keyring to remember SSH key passphrase.**

---

### Post by ChAoS.ct on 2010-11-12
I have exactly the same problem. I think since Maverick there no longer is a checkbox for remembering passphrases of SSH keys :S (previously it was like [http://ubuntuforums.org/attachment.php?attachmentid=113083&d=1241893284](http://ubuntuforums.org/attachment.php?attachmentid=113083&d=1241893284))

---

