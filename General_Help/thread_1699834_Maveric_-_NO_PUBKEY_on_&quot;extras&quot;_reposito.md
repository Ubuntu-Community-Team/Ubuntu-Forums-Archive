---
title: "Maveric - NO_PUBKEY on &quot;extras&quot; repository"
date: 2011-03-04
forum: General Help
---

### Post by _0R10N on 2011-03-04
I want to share with you the solution I found for a problem I had for some days, when trying to update my repositories.

Error message: 

```

W: GPG error: http://extras.ubuntu.com maverick Release: The following  signatures couldn't be verified because the public key is not available:  NO_PUBKEY XXXXXXXXXXXX

```

Solution:

Run the following command
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192
``` That will solve the issue and then you will be able to update your repositories successfully.

Hope this help!

Kind regards!

---

### Post by bobcollard on 2011-03-04
Actually that works on all pubkey not just Maverick.  I keep a copy of that solution in my Documents and just add the numbers to run it in Terminal.  Worked for many different distros for over a year and a half now.

---

