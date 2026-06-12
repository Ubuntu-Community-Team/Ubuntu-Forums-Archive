---
title: "OpenVPN"
date: 2011-11-26
forum: General Help
---

### Post by Dmatt on 2011-11-26
To whom it may concern,

I have configure an openvpn server, but when is do a restart on the service it says failed.  Can anyone help me?  A fast response would be great.

Thank You,
Dmatt

---

### Post by SeijiSensei on 2011-11-26
No one can help much if you don't give us more information than that!  How about logs?

One simple recurring error is the name of the group under which OpenVPN runs on Ubuntu.  RedHat-flavored installations use group "nobody" while Debian-flavored installations like Ubuntu use group "nogroup".

---

