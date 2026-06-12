---
title: "Run Scripts after each new Kernel"
date: 2010-09-06
forum: General Help
---

### Post by Sub101 on 2010-09-06
Hi all,

My laptop is a M11x and in order to get the audio working I must reinstall the Realtek driver for each new kernel.

Is there any way to trigger this automatically? Something like; On new kernel installed -> run script.

Thanks for your time.

---

### Post by dcstar on 2010-09-07
> **Sub101 said:**
> Hi all,

My laptop is a M11x and in order to get the audio working I must reinstall the Realtek driver for each new kernel.

Is there any way to trigger this automatically? Something like; On new kernel installed -> run script.

Thanks for your time.

This file contains commands to run after various kernel events (like updating Grub etc):

```
/etc/kernel-img.conf
```

I would try adding in another "postinst_hook =" command.

[http://www.tin.org/bin/man.cgi?section=5&topic=kernel-img.conf](http://www.tin.org/bin/man.cgi?section=5&topic=kernel-img.conf)

---

### Post by pbrane on 2010-09-07
Another way is to create a bash script to install your Realtek driver and then place it in the */etc/kernel/postinst.d/* directory. the kernel install deb package will run any scripts found here after the kernel is installed.

---

