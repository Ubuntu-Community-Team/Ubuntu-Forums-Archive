---
title: "gnumeric error"
date: 2009-12-13
forum: General Help
---

### Post by ajy0852 on 2009-12-13
I'd like to try Gnumeric. After I install it from the repositories (on Ubuntu 9.10), when I try to run it I get the following error:

```
gnumeric: symbol lookup error: /usr/lib/libspreadsheet-1.9.9.so: undefined symbol: foo_canvas_item_request_update
```

That libspreadsheet file is installed/uninstalled along with Gnumeric.

Does anyone have any ideas? The program will not run.

---

### Post by jbrefort on 2009-12-14
It seems that you have an incompatible goffice version (actually this is a certitude, FooCanvas was removed in goffice-0.7.10).

---

### Post by ajy0852 on 2009-12-14
Thanks for the reply. I had Abiword installed from a PPA which caused the incompatibility. I removed it, got rid of the PPA, and reinstalled abiword and gnumeric, both from the official repo's, now it works great. Thanks again.

> **jbrefort said:**
> It seems that you have an incompatible goffice version (actually this is a certitude, FooCanvas was removed in goffice-0.7.10).

---

### Post by guiodic on 2009-12-21
hi, i updated gnumeric in the same repository [https://launchpad.net/~guido-iodice/+archive/abiword-2.8](https://launchpad.net/~guido-iodice/+archive/abiword-2.8)

please check it.

---

