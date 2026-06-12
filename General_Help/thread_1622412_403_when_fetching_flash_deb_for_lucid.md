---
title: "403 when fetching flash deb for lucid"
date: 2010-11-15
forum: General Help
---

### Post by imbjr on 2010-11-15
Anyone else get a 403 for:

[http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-1lucid1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-1lucid1_i386.deb)

---

### Post by pqwoerituytrueiwoq on 2010-11-15
you can get a deb installer for 32bit on adobes site

---

### Post by jwbrase on 2010-11-15
Yes.

---

### Post by imbjr on 2010-11-15
> **pqwoerituytrueiwoq said:**
> you can get a deb installer for 32bit on adobes site

Mmm, I wonder if it will do automatic updates tho? I'd rather the standard way work rather than go through this route.

Who do we contact to get stuff like this fixed?

Edit: found a webmaster e-mail address for canonical.

---

### Post by gandaran on 2010-11-15
> **imbjr said:**
> Anyone else get a 403 for:

[http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-1lucid1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-1lucid1_i386.deb)
you are not alone with this problem but you could remove the canonical flash package and install the ubuntu supported adobe flash (flashplugin-installer) package instead.

---

### Post by luigi_mb on 2010-11-15
In your software sources change to "Main" server.

/luigi

---

### Post by Enigmapond on 2010-11-15
> **luigi_mb said:**
> In your software sources change to "Main" server.

/luigi

This doesn't work...at least for Lucid. After the change it gave a "malformed" error so I chnaged it back. As it is, it checks the repo ok but only when it goes to download does the error come up...

---

### Post by imbjr on 2010-11-16
> **Enigmapond said:**
> This doesn't work...at least for Lucid. After the change it gave a "malformed" error so I chnaged it back. As it is, it checks the repo ok but only when it goes to download does the error come up...

Agreed. It makes no difference. I will try the installer package instead.

---

### Post by imbjr on 2010-11-16
> **imbjr said:**
> Agreed. It makes no difference. I will try the installer package instead.

Looks like the webmaster has fixed the problem; the deb file is downloadable.

---

