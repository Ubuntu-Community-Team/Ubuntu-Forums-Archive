---
title: "convert virtualbox hard disk to qemu compatible"
date: 2009-09-06
forum: General Help
---

### Post by pythonscript on 2009-09-06
How do I convert a virtualbox hard disk (.VDI) to something compatible with qemu (.IMG, I believe)? I found a source elsewhere on the internet that had me using

```
qemu-img convert image.vmdk image.bin
VBoxManage convertdd image.bin image.vdi

```

These were the steps to do so under Arch Linux, and they worked great on my desktop's arch installation. Are these same commands for ubuntu? I thought I'd ask before I tried it on my main XP installation image. Thanks!

---

### Post by pythonscript on 2009-09-08
Anyone have any ideas? This would definitely beat reinstalling and reconfiguring my entire win xp installation from virtualbox to qemu. Thanks!

---

