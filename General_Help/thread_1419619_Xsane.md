---
title: "Xsane"
date: 2010-03-02
forum: General Help
---

### Post by cowboy7305 on 2010-03-02
Iam using xsane to try and scan a document to computer my scaner is a HP photosmart c3180 it only wants to scan part of document has any one found a way to get round this  many thanks

---

### Post by thebigob on 2010-03-02
I recently had this problem.

If the scanner is not doing the whole length of the scanner (i.e. it wont go the whole way down) then it could be something similar to my problem.

In my case I was using the wrong driver:

The driver will be located in something similar to /usr/share/sane/artec_eplus48u

in your case /usr/share/sane/"insert manufacturer here"

the config file mentioning the driver will be here /etc/sane.d/artec_eplus48u.conf

again in your case /etc/sane.d/"insert model here"

I would check that it is pointing to the right driver.

Hope this is of some use :)

---

### Post by syncmasterpt on 2010-03-02
Goto the HPLIP site and download the latest driver version for your printer. Install it and try again, to see if the issue is solved.

---

