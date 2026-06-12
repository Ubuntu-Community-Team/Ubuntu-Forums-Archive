---
title: "conky memory usage off"
date: 2009-12-31
forum: General Help
---

### Post by chrisbraddock on 2009-12-31
Yesterday I started noticing conky reporting very high memory% in-use.  I fired up System Monitor to see what was hogging the memory and it didn't show the same results that conky did.  (screenshot attached)

Can anyone help explain the discrepancy?

---

### Post by kpkeerthi on 2009-12-31
Add this option to your .conkyrc
```

# Subtract file system buffers from used memory?
no_buffers yes

```

---

### Post by chrisbraddock on 2009-12-31
Perfect - thanks!

---

