---
title: "API mismatch"
date: 2012-05-17
forum: General Help
---

### Post by Cardale on 2012-05-17
kernel log error

17/05/12 04:50:49 PM    NVRM    API mismatch: the client has the version 290.10, but
17/05/12 04:50:49 PM    NVRM    this kernel module has the version 295.40. Please
17/05/12 04:50:49 PM    NVRM    make sure that this kernel module and all NVIDIA driver
17/05/12 04:50:49 PM    NVRM    components have the same version.

How can I repair this?

---

### Post by Cardale on 2012-05-18
I tried reinstalled and completely purging everything, but I just can't fix it.  How can I get rid of this?

---

### Post by Cardale on 2012-05-18
This is an annoying way to fix the issue, but if you download the Nvidia drivers and install them then remove them with the Nvidia uninstaller you can solve this issue.

The nvidia drivers actually detect the mismatch and fix it. 

I think we need to do this in our packaging.

---

