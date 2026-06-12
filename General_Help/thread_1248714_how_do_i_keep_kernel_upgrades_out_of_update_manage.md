---
title: "how do i keep kernel upgrades out of update manager?"
date: 2009-08-24
forum: General Help
---

### Post by Bubs on 2009-08-24
Hi 

I just did a fresh install of UNR on an acer aspire one netbook and also installed the custom kuki kernel for AAO netbooks.  

I'm wondering how I can keep the generic kernel upgrades out of the update manager?

---

### Post by Brandon Williams on 2009-08-24
The kernel image and the restricted modules are both update via changes to a couple of high-level metapackages. If you remove linux-generic, linux-image-generic, linux-restricted-modules-generic, then the kernel image and restricted modules will no longer be updated automatically.

---

### Post by Slim Odds on 2009-08-24
Why would you want to do this?

---

### Post by bodhi.zazen on 2009-08-24
> **Slim Odds said:**
> Why would you want to do this?

Because he is running a custom kernel.

> **Bubs said:**
> Hi 

I just did a fresh install of UNR on an acer aspire one netbook and also installed the custom kuki kernel for AAO netbooks.  

I'm wondering how I can keep the generic kernel upgrades out of the update manager?

See this linky :

[http://www.ubuntugeek.com/how-to-prevent-a-package-from-being-updated-in-ubuntu.html](http://www.ubuntugeek.com/how-to-prevent-a-package-from-being-updated-in-ubuntu.html)

---

### Post by scouser73 on 2009-08-24
Go to **Synaptic Package Manager**, locate the kernels that you do not want, highlight them, click **Package**, select **Lock Version** and then click **Apply**.

---

### Post by kerry_s on 2009-08-24
> **scouser73 said:**
> Go to **Synaptic Package Manager**, locate the kernels that you do not want, highlight them, click **Package**, select **Lock Version** and then click **Apply**.

shouldn't he be able to uninstall the standard kernel?
i mean he has his own, those would just be extra.

---

