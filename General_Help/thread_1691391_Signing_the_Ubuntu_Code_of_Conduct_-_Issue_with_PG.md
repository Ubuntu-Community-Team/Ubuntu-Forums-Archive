---
title: "Signing the Ubuntu Code of Conduct - Issue with PGP Key?"
date: 2011-02-19
forum: General Help
---

### Post by mr_luksom on 2011-02-19
I have no idea which forum to post this is, so I'll give it a go here.

I'm having trouble signing the Ubuntu Code of Conduct. I get my key using 

```

gpg -- fingerprint

```

And I copy the 40 hex digit key into the the OpenPGP key box, however I get the message:

The key <<Key Removed for privacy>> has already been imported.

I am 100% sure I have not registered the key (I can't skip the step and just sign the CoC).

Does this mean that there are identical keys? Can I get a new one?

---

### Post by mr_luksom on 2011-02-20
I created a new key using the "Passwords and Keys" tool in the preferences menu, that solved the issue.

---

