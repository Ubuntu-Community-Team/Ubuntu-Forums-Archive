---
title: "GPG / Seahorse Broken?"
date: 2009-12-02
forum: General Help
---

### Post by pmunly on 2009-12-02
I'm using UNR 9.10 and am having issues with GPG / Seahorse.  At this point I'm not sure if something is misconfigured or if there is a bug within either GPG, Seahorse (specifically seahorse-tool), or something else that effects the password/pin entry when encrypting or decrypting files.

With that said, this is something relatively recent as approximately 3 weeks ago I was able to encrypt/decrypt files using seahorse with no issues.  Currently my system is up-to-date with all the "non-pre-release" patches available via update-manager. The issue is this:  

When attempting to encrypt (and sign) or decrypt a file through the nautilus, the pinentry opens, then closes almost immediately, then opens again stating the password was incorrect, then closes a second, and third time.  After this, a window opens stating the file was unable to be encrypted due to an incorrect password.  Since that didn't work, I tried running:

$ gpg2 -e -s "myfile"

from the command line.  This resulted in a GUI pinentry window opening and closing immediately and the following message on the command line:

You need a passphrase to unlock the secret key for
user: "<my user name and email>"
1024-bit DSA key, ID <my key id>, created 2008-06-22

gpg: problem with the agent: IPC write error
gpg: Invalid passphrase; please try again ...

You need a passphrase to unlock the secret key for
user: "<my user name and email>"
1024-bit DSA key, ID <my key id>, created 2008-06-22

gpg: problem with the agent: Not supported
gpg: no default secret key: General error
gpg: "myfile": sign+encrypt failed: General error

Any help with this issue would be greatly appreciated.  If it's a bug, I'll file it, I just need help determining if this is in fact a bug with the seahorse or gpg programs, or just something misconfigured on my end.

---

### Post by meonkeys on 2009-12-23
Here are a couple bugs that may be related:
[LIST]
[*][https://bugs.launchpad.net/bugs/383256](https://bugs.launchpad.net/bugs/383256)
[*][https://bugs.launchpad.net/bugs/183514](https://bugs.launchpad.net/bugs/183514)
[/LIST]

---

### Post by vhex on 2010-06-11
To fix this problem you can open gconf-editor, navigate to apps/maximus and add "pinentry" to the exclude_class key. Thanks to Martin Webster,

[http://martinwebster.info/2010/05/21/entering-an-openpgp-passphrase-on-ubuntu/](http://martinwebster.info/2010/05/21/entering-an-openpgp-passphrase-on-ubuntu/)

---

