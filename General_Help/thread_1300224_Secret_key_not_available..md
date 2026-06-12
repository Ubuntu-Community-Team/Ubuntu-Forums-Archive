---
title: "Secret key not available."
date: 2009-10-24
forum: General Help
---

### Post by Johansen on 2009-10-24
[RANT] Hello,  I recently registered to find help for a simple bug, yet one that 6 hours of googling hasn't solved.  I have found an old thread from 2005 however, with the exact same problem. [Link]("http://ubuntuforums.org/showthread.php?t=58054&") 

> highlight=secret+key+not+available    
[..]
I'm trying to use GnuPG with either evolution and enigmail in thunderbird, but no one of both are working . . .  GnuPG seem to work fine in terminal, as I generate a key, -- list-key show me the key correctly.  evolution error message:  Code:  Impossible to create the message, cause "gpg: skipped '0x330BB...' : secret key not available. gpg: signing failed: secret key not available  Enigmail error message: Code:  Send operation aborted  Error -encryption command failed  gpg command line and output: /usr/bin/gpg --charset utf8 --batch --no-tty --status-fd 2 --clearsign --digest-algo sha1 -u  --passphrase-fd 0 --no-use-agent  gpg: skipped  : secret key not available gpg: [stdin]: clearsign failed: secret key not availableWhat mine says:
Error - Encryption command failed
gpg: skipped "0x8703820E": secret key not available.
gpg: [stdin]: clearsign failed: secret key not available. 

The kicker:
I deleted that key and made a few new ones, even specified that the new keys be set as default in gpg.conf and options.skel

the only thing I have not tried is purging and reinstalling thunderbird, which i would rather not do for obvious reasons.

question: where are all the possible conflicting config files that might have a reference to the old key? 
Also, I can encrypt to my own secret key and decrypt the message, but I cannot sign a message with any key due to the above error.

During the course of typing this, I imported 20-30 puplic keys and deleted the public key 0x8703820E you see above.  Now when I encrypt to the new keys, it tells me that it can't because it can't find the public key 0x8703820E
INV_RECP


also, i discovered what caused this in my case.
thunderbird> account settings>> openPGP>> use specific key
*was still set to the old key

THIS IS NOT AT ALL INTUITIVE. As I had looked through all the .conf files in Thunderbird looking for any referenced to the key in question.

I will copy and paste this into the enigmail forum when i can read the confirmation code.

[/RANT]

---

