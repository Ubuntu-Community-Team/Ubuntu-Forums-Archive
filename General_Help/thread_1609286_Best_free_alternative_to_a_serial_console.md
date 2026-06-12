---
title: "Best free alternative to a serial console?"
date: 2010-10-30
forum: General Help
---

### Post by bitmonkey on 2010-10-30
I've been thinking recently it would be good to have pre-boot access over the network to my servers (only a few) to fix boot problems remotely. What are my options in the free or VERY cheap categories?

I've seen network console software which can start as soon as the root filesystem mounts read only, but I'd like to have the option of getting access earlier than that. The USB serial solutions and a console server have 2 disadvantages I can see - one more box in the machine cupboard, and they still don't get you in pre root-fs unless you can do hardware console redirection from the BIOS or a custom card neither of which are possible for me.

It may be a silly question - I'm not untechnical, but I don't know a great deal about the boot process yet - is there any way I can get networking up and a software serial console emulation layer running in the /boot partition so I can get on remotely if the root filesystem fails to mount?

---

