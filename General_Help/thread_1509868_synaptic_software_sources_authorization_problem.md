---
title: "synaptic software sources authorization problem"
date: 2010-06-14
forum: General Help
---

### Post by Vined Adobo on 2010-06-14
When I try to update my wife's netbook, I get this error:

[INDENT]W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF

[/INDENT]When I look at the authentication tab, there is no entry for that key.

On my laptop, however, I get no error, and the update runs smoothly.  Also, in my authentication tab, I do get the entry referring to key 46D7E7CF.  

Neither machine is on a proxy and both use the same software server.

Any ideas?

Thanks,
Dave

---

### Post by howefield on 2010-06-14
Have you tried adding the key as described here

[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)

---

### Post by Vined Adobo on 2010-06-14
> **howefield said:**
> Have you tried adding the key as described here

[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)


Worked like a charm!.  The first line was already there.  The key just disappeared for some reason.


Thank you very much!

Dave

---

### Post by howefield on 2010-06-14
> **Vined Adobo said:**
> Worked like a charm!.

I like good news.. :)

Thanks for the update.

---

