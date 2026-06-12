---
title: "Compression."
date: 2010-01-10
forum: General Help
---

### Post by zozza on 2010-01-10
Having just compressed with tar and gzip bzip2 and compress a 500MB file there seems to be limited difference in results.

Gzip and Compress both come out at 295MB while Bzip is 285MB.  

For large files can anyone recommend me something that compresses better - if one exists that is?

Thanks.

---

### Post by The Cog on 2010-01-10
No. bzip gives very good compression, but at the cost of more time and CPU than gzip. Bear in mind that how compressible a file is depends on the file contents. You are unlikely to achieve better compression than you already have.

---

