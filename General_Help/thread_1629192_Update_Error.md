---
title: "Update Error"
date: 2010-11-23
forum: General Help
---

### Post by Vistz on 2010-11-23
When I try to do 
```
sudo apt-get update
```

the last line says ```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D225991A72B194E5

```

I've tried the method described here: ```
http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html
```

However, I'm still getting the same error. Any advice?

---

### Post by sikander3786 on 2010-11-23
Go to Software Center > Edit > Software Sources > Other Software Tab and disable the offensive PPA. Then try apt-get update again.

---

### Post by Vistz on 2010-11-23
> **sikander3786 said:**
> Go to Software Center > Edit > Software Sources > Other Software Tab and disable the offensive PPA. Then try apt-get update again.

Thank you. That did it.

---

