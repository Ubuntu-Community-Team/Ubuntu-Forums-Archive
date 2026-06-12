---
title: "Extremely large initrd after compiling kernel"
date: 2011-06-20
forum: General Help
---

### Post by towheedm on 2011-06-20
I finally built my first kernel using the latest stable release (2.6.39.1) from kernel.org.
The kernel is booting fine and I also got the NVIDIA proprietary drivers installed and working.

The thing is that my new initrd file is 126MB compared to 16MB for the 2.6.35.28-generic kernel.  Both are gzipped from the .config file.  I used the .config file from the 2.6.35.28-generic kernel and simply set the new options.

Any idea why the new initrd is so large?

How can I test the performance of the new kernel?

---

