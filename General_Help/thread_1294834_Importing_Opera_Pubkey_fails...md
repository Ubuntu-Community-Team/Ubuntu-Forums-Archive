---
title: "Importing Opera Pubkey fails.."
date: 2009-10-18
forum: General Help
---

### Post by sports fan Matt on 2009-10-18
fails with W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

Is it not needed..I was gonna add it to my launchpad keys?.

---

### Post by Bachstelze on 2009-10-18
Have you done this?

```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -

```

---

### Post by sports fan Matt on 2009-10-18
I had before and did it a second time and the 2nd time it worked..strange how that occurs :)

---

