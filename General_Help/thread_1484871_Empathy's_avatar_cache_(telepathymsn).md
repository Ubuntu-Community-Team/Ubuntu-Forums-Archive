---
title: "Empathy's avatar cache (telepathy/msn)"
date: 2010-05-16
forum: General Help
---

### Post by T0mmy on 2010-05-16
I'm trying to convert some of my old Pidgin-logs to Empathy's format, and I've run into an issue I can't figure out. The Empathy logfiles contain a "token", which is a sha1-hash of the user's avatar at the moment the message was sent.

The avatars are stored (in my case) in ~/.cache/telepathy/avatars/butterfly/msn. All filenames contain the sha1-hash, and have no extension (such as jpg/png). Some avatars uses only the hash as filename, but some has the prefix "_3" before the hash.

Does anyone know why some avatars are prefixed "_3"?

I do not see any consistency regarding filetype (jpg/png) or filesize, but the prefix seems crucial when linking the logged message to a cached avatar:
Cache: hash / Log-token: hash | Works
Cache: _3hash / Log-token: _3hash | Doesn't work
Cache: _3hash / Log-token: hash | Works (but why? as the filename doesn't match?)
Cache: hash (renamed from _3hash) / Log-token: hash | Doesn't work

Hopefully some of you might know the answer, or where I can find it...

---

### Post by T0mmy on 2010-05-16
I think I just figured it out:

- If the hash starts with a number, the prefix "_3" is added to the hash in the filename.
- If the hash starts with a letter, the hash is used as filename without the prefix.

Could someone please verify this?

---

### Post by dearingj on 2010-05-16
> **T0mmy said:**
> I think I just figured it out:

- If the hash starts with a number, the prefix "_3" is added to the hash in the filename.
- If the hash starts with a letter, the hash is used as filename without the prefix.

Could someone please verify this?

I can confirm it. I just checked my Empathy's avatar cache and saw the same pattern. It appears this is not specific to MSN, as I only use Google Talk.

---

### Post by T0mmy on 2010-05-16
Thanks!

---

