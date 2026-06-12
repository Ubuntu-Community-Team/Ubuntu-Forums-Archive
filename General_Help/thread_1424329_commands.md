---
title: "commands"
date: 2010-03-07
forum: General Help
---

### Post by inoh on 2010-03-07
what is the lsusb equivalent of lspci -k?

---

### Post by mechro on 2010-03-07
**man lsusb** tells me there isn't an equivalent.

**sudo lsusb -v** will give you all the information. Presumably you could grep the output down to an lspci -k equivalent if you know what details you require.

---

