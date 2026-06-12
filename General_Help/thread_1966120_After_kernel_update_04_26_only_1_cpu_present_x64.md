---
title: "After kernel update 04 26 only 1 cpu present x64"
date: 2012-04-26
forum: General Help
---

### Post by Gedablo on 2012-04-26
So today ive updated my system via update manager. There was a new kernel as ive noticed. after that ive checked hows my cpu doing, and i got 3 cpus missing. Im using intel core i3 330m . Ubuntu 12.04 x64 on the main system(not virtual machines). What could be the problem?

Edit. i have fixed it by changing lines acpi=on in boot/grub/grub.cfg

---

### Post by Bobhuber on 2012-04-26
> **Gedablo said:**
> So today ive updated my system via update manager. There was a new kernel as ive noticed. after that ive checked hows my cpu doing, and i got 3 cpus missing. Im using intel core i3 330m . Ubuntu 12.04 x64. What could be the problem?
Is this in virtualbox ?

---

### Post by Gedablo on 2012-04-26
i have fixed it by changing lines acpi=on in boot/grub/grub.cfg

---

