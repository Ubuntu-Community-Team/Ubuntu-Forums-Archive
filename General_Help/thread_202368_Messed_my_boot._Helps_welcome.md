---
title: "Messed my boot. Helps welcome"
date: 2006-06-23
forum: General Help
---

### Post by panurge77 on 2006-06-23
I installed kubuntu-desktop over my ubuntu. I chose to stick with gdm when the installation asked me. It was all fine, except for BUM was showing me kdm was up and not gdm. I disabled kdm and enabled gdm~. It was still fine, but then I went to sysv-rc-conf to see all the details. Then I found two gdms. A gdm and a gdm~. I disabled one of them, and now I get a kernel panic when booting. How can I run sysv-rc-conf on my hd partition from the live cd? Or any other workaround?

---

### Post by panurge77 on 2006-06-23
Ok. I changed the names of both gdm scripts so the boot would no find them. And then I booted into command line and enabled both again. Anyway... does anyone one knows why was bum showing me kdm?

---

### Post by panurge77 on 2006-06-23
Looks like I only need gdm~, which is probably the old gdm. So... does kde changes my gdm so that it depends on kdm? :-k

---

