---
title: "How to configure Kernel"
date: 2006-05-17
forum: General Help
---

### Post by jsmidt on 2006-05-17
I am trying to install a wireless driver.  The instructions say this:

The ipw3945 driver will look for the file ipw3945.ucode using the
kernel's firmware_loader infrastructure.  In order to function
correctly, you need to have this support enabled in your kernel.  When
you configure the kernel, you can find this option in the following
location:

        Device Drivers ->
                Generic Driver Options ->
                        Hotplug firmware loading support


You can determine if your kernel currently has firmware loader support
by looking for the CONFIG_FW_LOADER definition on your kernel's
.config.



How can I go about doing this?

---

