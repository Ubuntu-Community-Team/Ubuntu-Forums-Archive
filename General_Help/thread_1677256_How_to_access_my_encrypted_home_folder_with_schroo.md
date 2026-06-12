---
title: "How to access my encrypted home folder with schroot?"
date: 2011-01-28
forum: General Help
---

### Post by zo_zo on 2011-01-28
Hi,

I created a chroot environment to run a 32-bit application on my 64-bit computer. However, my home folder is encrypted (encryptfs), and when I try to enter the new environment with schroot I receive warnings and am redirected to the /root folder.

So my question is how can I access my home folder? I tried to change the mount point in /etc/schroot/mount-defaults by mounting /home/user/.Private in the /home/user folder but I then get a list of encrypted files.

Many thanks for your suggestions!

---

### Post by dpm on 2011-04-28
You might be interested in following the progress of this bug: [https://bugs.launchpad.net/ecryptfs/+bug/759569](https://bugs.launchpad.net/ecryptfs/+bug/759569)

---

