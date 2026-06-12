---
title: "How do I get the volume control to show in top panel?"
date: 2010-09-12
forum: General Help
---

### Post by joelw135 on 2010-09-12
For some reason my volume control disappeared from the top panel, how do I get it back?

---

### Post by mirchichamu on 2010-09-12
> **joelw135 said:**
> For some reason my volume control disappeared from the top panel, how do I get it back?

write the following command in terminal and the restart the system:

code:  gconftool-2 --recursive-unset /apps/panel

---

### Post by joelw135 on 2010-09-12
> **mirchichamu said:**
> write the following command in terminal and the restart the system:

code:  gconftool-2 --recursive-unset /apps/panel

Thanks, that did the job.

---

### Post by mirchichamu on 2010-09-12
> **joelw135 said:**
> Thanks, that did the job.

Happy that your problem solved...mark the thread as SOLVED.

---

