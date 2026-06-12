---
title: "SSL Error 61 - Citrix ICA - Firefox"
date: 2010-08-02
forum: General Help
---

### Post by Trace123 on 2010-08-02
The Linux client from Citrix is missing a root certificate authority. Copy the root certificates from your browser - Mozilla - into your ICA client CA certificate folder by entering the command below
"cp /usr/share/ca-certificates/mozilla/* /usr/lib/ICAClient/keystore/cacerts/"

This should resolve the issue of not being able to access published applications or Desktop resources.

---

