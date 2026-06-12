---
title: "Problems with vmware after upgrade"
date: 2006-05-30
forum: General Help
---

### Post by [S|G] on 2006-05-30
Hello, I updated my system using adept (as I usually do nearly every day) but afterwards I was unable to run VMWare. I'm getting these errors:
```

/opt/vmware/bin/vmware: /opt/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/opt/vmware/bin/vmware: /opt/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/opt/vmware/bin/vmware: /opt/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/opt/vmware/bin/vmware: /opt/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/opt/vmware/bin/vmware: /opt/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/opt/vmware/bin/vmware: /opt/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

```

I'm going to try to re-install vmware... but anyone has any ideas? By the way, I do have gcc-3.4 and gcc-3.4-base installed on my system. Also the files on vmware/lib do exist, and the whole directory is readable to all users.

---

### Post by Triton on 2006-05-30
Has the kernel been updated?

---

### Post by [S|G] on 2006-05-30
The strange part is that it wasn't. The last time I updated my kernel I had vmware recompile its modules. But this time not even recompiling makes it work.

---

