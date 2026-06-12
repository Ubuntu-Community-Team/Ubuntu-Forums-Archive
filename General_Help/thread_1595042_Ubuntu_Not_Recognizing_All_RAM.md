---
title: "Ubuntu Not Recognizing All RAM"
date: 2010-10-12
forum: General Help
---

### Post by Precipitous on 2010-10-12
I just installed Maverick Studio on a new hard drive. My computer has 4GB of RAM, but the OS is only reporting that I have 3GB. When I boot, if I run the MemTest+, all 4GB are reported, and all tests run perfectly with no errors. Before I replaced the hard drive, I was running Lucid, and it saw all 4GB as well. Does anybody know what is causing this?

---

### Post by Precipitous on 2010-10-13
> **Precipitous said:**
> I just installed Maverick Studio on a new hard drive. My computer has 4GB of RAM, but the OS is only reporting that I have 3GB. When I boot, if I run the MemTest+, all 4GB are reported, and all tests run perfectly with no errors. Before I replaced the hard drive, I was running Lucid, and it saw all 4GB as well. Does anybody know what is causing this?
This was solved by installing and running the PAE version of the kernel instead of the regular one.

---

