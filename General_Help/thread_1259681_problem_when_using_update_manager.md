---
title: "problem when using update manager"
date: 2009-09-06
forum: General Help
---

### Post by chkneater on 2009-09-06
Hi, whenever I use update manager I get a warning box with this dialogue:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I'm using 8.04, and I get this code when I check for available updates

---

### Post by cmost on 2009-09-06
This is meaningless.  It simply means you haven't installed the repository's signing key.  No biggie.  I get well over a dozen of these errors whenever I update my sources since I have a lot of third party repositories enabled and I won't be bothered to add the various GPG keys.  Either add the key to make the error go away or ignore it.  Either way, no harm.

---

### Post by chkneater on 2009-09-06
Thanks Cmost, that's kinda what I thought it was.  how do I add the key?

---

### Post by cmost on 2009-09-06
Most repositories provide the key as a cryptic number (you'll most likely see it in the error itself, or you can google the repository and see if the key shows up somewhere.)  Once you get the key, you can add it to your keyring as so...

gpg --keyserver subkeys.pgp.net --recv (put the code at the end here)
gpg --export --armor (enter same above code) | sudo apt-key add -

---

