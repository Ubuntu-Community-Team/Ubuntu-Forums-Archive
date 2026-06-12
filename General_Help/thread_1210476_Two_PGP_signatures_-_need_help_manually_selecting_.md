---
title: "Two PGP signatures - need help manually selecting one"
date: 2009-07-11
forum: General Help
---

### Post by guv999 on 2009-07-11
Hi 
I am attempting to sign the code of conduct, and ended up creating two different PGP fingerprints linked to different email addresses.   
I am now attemting to use the 

gpg --clearsign UbuntuCodeofConduct-1.0.1.txt

command to sign the document, but have noticed that the terminal is using the alternate PGP fingerprint that has not been used for the other steps in the process.
When I attempt to pen the asc document created I receive an error message advising:
Couldnt verify file - no valid signatures found

Can anyone advise how I can ensure that the appropriate PGP fingerprint  is selected?  Thanks

---

