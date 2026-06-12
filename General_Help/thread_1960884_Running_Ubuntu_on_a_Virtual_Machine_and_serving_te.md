---
title: "Running Ubuntu on a Virtual Machine and serving test websites locally"
date: 2012-04-18
forum: General Help
---

### Post by kev670q on 2012-04-18
I want to run ubuntu server on a virtual machine on windows 7 and then test websites on windows that are served by the virtual machine through localhost or something similar on windows... Is this possible and if so can you point me to how...

Also i should i use vmware player or server or ...

Thanks

---

### Post by haqking on 2012-04-18
> **kev670q said:**
> I want to run ubuntu server on a virtual machine on windows 7 and then test websites on windows that are served by the virtual machine through localhost or something similar on windows... Is this possible and if so can you point me to how...

Also i should i use vmware player or server or ...

Thanks

Install Apache onto your server.

Give the VM a static IP valid for your Lan and choose bridged networking for the VM settings.

Then point your browser to that IP.

If its for home then Virtualbox will be fine, or vmware player

---

