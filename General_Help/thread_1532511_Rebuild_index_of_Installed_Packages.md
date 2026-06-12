---
title: "Rebuild index of Installed Packages"
date: 2010-07-16
forum: General Help
---

### Post by frogotronic on 2010-07-16
Hi,

  Been trying to report program crashes via apport, but am getting this error:

```
Thank you for your report!

However, processing it in order to get sufficient information for the
developers failed (it does not generate an useful symbolic stack trace). This
might be caused by some outdated packages which were installed on your system
at the time of the report:

libpam-modules: installed version 1.1.0-2ubuntu1, latest version: 1.1.0-2ubuntu1.1
libpam0g: installed version 1.1.0-2ubuntu1, latest version: 1.1.0-2ubuntu1.1
libpam-runtime: installed version 1.1.0-2ubuntu1, latest version: 1.1.0-2ubuntu1.1
libpng12-0: installed version 1.2.37-1ubuntu0.1, latest version: 1.2.37-1ubuntu0.2


Please upgrade your system to the latest package versions. If you still
encounter the crash, please file a new report.

Thank you for your understanding, and sorry for the inconvenience!
```

After checking Synaptic, I actually do have the latest packages installed, but I guess there is an index that is not (was not) updated.

How do I reindex the installed packages?

- CH

---

