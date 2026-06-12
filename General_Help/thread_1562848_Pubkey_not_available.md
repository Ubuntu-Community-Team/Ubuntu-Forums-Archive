---
title: "Pubkey not available"
date: 2010-08-28
forum: General Help
---

### Post by tomopotamus on 2010-08-28
Earlier this morning, I ran the update command in the terminal and at the end of the update, I saw the following:

```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 46B4E34C17CF995E
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8CA7A6E8E4FA953A

```

This is the first time I have ever seen this before.  What does this mean exactly?  Is this something that I should worry about and how can it be corrected?

Thanks for your help!

---

### Post by Silent Warrior on 2010-08-28
It just means you didn't get the digital signatures with the PPA-repositories you installed. I get that myself, too. The only direct problem is that you can't verify that the packages you download from the concerned repository (good luck finding out which one, though - the error message only lists the main server, where, incidentally, each and every PPA reside). Which in turn means that you technically can't trust those packages. *Shrug* Either go over your added PPAs and re-add them properly one by one using the proper commands, or just carry on regardless. How secure do you want to be?

---

### Post by lmarmisa on 2010-08-28
Maybe this link can help you:

[http://stream-recorder.com/forum/w-gpg-error-http-ppa-launchpad-net-t6741.html?](http://stream-recorder.com/forum/w-gpg-error-http-ppa-launchpad-net-t6741.html?)

---

