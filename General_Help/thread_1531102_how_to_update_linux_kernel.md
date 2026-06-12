---
title: "how to update linux kernel?"
date: 2010-07-14
forum: General Help
---

### Post by agent_509 on 2010-07-14
How do I update my linux kernel?

---

### Post by sanderd17 on 2010-07-14
the kernel updates come with all other updates in ubuntu. via the update manager.

You do need to restart after a kernel update.

Do only try to update to a testing kernel on a machine that you use to test, not on your regular machine.

---

### Post by cj.surrusco on 2010-07-14
When there is an update available for the kernel, it will appear in the Update Manager and will automatically update when you choose to update.

---

### Post by WorMzy on 2010-07-14
You should be automatically be prompted to update whenever Canonical add an update to the update repo - assuming, of course, you've got that repo checked in your software sources (System -> Administration -> Software Sources) and have the 'linux-image' package installed (which you do be default). Canonical always seem to stay two or three releases behind the current kernel for whatever reason though, so if you want to have the most up-to-date kernel, you'll have to compile it yourself.

[http://www.google.co.uk/search?q=how%20to%20compile%20a%20linux%20kernel](http://www.google.co.uk/search?q=how%20to%20compile%20a%20linux%20kernel)

---

### Post by agent_509 on 2010-07-14
ok, thanks guys

---

### Post by ajgreeny on 2010-07-14
If you are prepared to take the risk ( small, I think) you can also use test kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Just search for those for your particular distro and try them out.  I have used the 2.6.34 final for lucid with no problems on a test install, but it did not solve the overheating problem so I removed it and still use the repository version, 2.6.32-23 at the moment.

---

