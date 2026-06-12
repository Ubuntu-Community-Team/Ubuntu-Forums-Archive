---
title: "Adding decrypt when rightclicking pgp/gpg files?"
date: 2006-06-04
forum: General Help
---

### Post by Eklöf on 2006-06-04
Is this possible. There is an encryption option there when I right-click a file but no decrypt when right-clicking the encrypted file..

---

### Post by dangermouse28 on 2006-10-27
I installed seahorse and found the exact same problem - encrypts fine to .pgp file but no decrypt option. Then discovered that if I changed the file extension to .gpg, the decrypt option became available in the context menu (right-click). It appears that .pgp files are not supported, but .gpg files are.:-k

---

### Post by sbassett on 2007-01-19
This appears to be an issue still with Edgy. Anyone found a solution to this yet? The open with when changing to .gpg is "Decrypt File", which does not when you want to associate to .pgp files.

huzzah and good show. It looks like "seahorse-tool -d" will do the trick when selecting open with other application..., then custom command, and entering the above. geesh, they make it tricky, don't they? Hope this helps someone.

p.s. - no quotes on seahorse-tool -d

---

### Post by fabertawe on 2007-02-13
> **sbassett said:**
> ...huzzah and good show. It looks like "seahorse-tool -d" will do the trick when selecting open with other application...

Thank you for this, it's been bugging me for ages! :KS 

Paul

---

