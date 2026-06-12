---
title: "grub2 weird behavior (timeout disappears)"
date: 2010-01-07
forum: General Help
---

### Post by tomhorsley on 2010-01-07
My ubuntu 9.10 virtual machines (hosted on KVM) have developed this annoying habit: Sometimes when my scripts try to boot the machine, grub will sit there waiting for someone to pick an entry to boot. Needless to say, the machine never appears to actually come up (which I define as talking ssh)  because no one is looking at the console. I check the /etc/default/grub file, and all the #defines are indeed setup as I last left them to have the generated grub.cfg boot the default config after a few seconds. If I touch /etc/default/grub and re-run the grub update tool, then the machine once again boots with the normal timeout. Has anyone else encountered self-modifying grub.cfg files? I have no idea how the timeout is getting disabled.

---

