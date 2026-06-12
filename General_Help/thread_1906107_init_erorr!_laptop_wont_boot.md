---
title: "init erorr! laptop wont boot?"
date: 2012-01-08
forum: General Help
---

### Post by amna543 on 2012-01-08
hi
I turned my computer on and it comes up with ways to boot and I clicked Ubuntu with linux 2.6.38-13-generic. There was a recovery mode too. Once I clicked its writing come up:

init: udevtrigger main process (93) terminated with status 1
init: udevtrigger post stop process (97) terminated with status 1
init: udevtrigger main process (92) killed by TERM signal
mountall: disconnected from plymouth
init: plymouth-splash main processs (98 ) terminated with status 2
init: plymouth main process (50) killed by SEGV signal
 
 I have no idea what this means and my laptop don't boot. I tried recovery mode but it comes up with similar things. I don't know why this has happened. It can be because I tried upgrading my Ubuntu to 11.0 and I shutdown the laptop before it finished? i would be most grateful if you could help
 amna

---

### Post by restorator on 2012-01-08
> It can be because I tried upgrading my Ubuntu to 11.0 and I shutdown the laptop before it finished?

Yes thats it! Its a very bad thing to lose power through any means during core changes for any system.

If you cannot even get into it via recovery mode you very likely have to do a fresh install. "Upgrades" (not updates) do not always go well due to many factors anyway. Hopefully you backed up your stuff before you tried to do the upgrade, but if you did not, then startup you computer via the live cd and see if you can access your files. If you can then you can back them up to another drive or partition and then do a fresh install.

---

