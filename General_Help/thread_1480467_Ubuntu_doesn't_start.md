---
title: "Ubuntu doesn't start"
date: 2010-05-11
forum: General Help
---

### Post by Anonim33 on 2010-05-11
My ubuntu doesn't start. After rebooting it's seem that splash screen is working without any results. I' ve deleted in grub menu "quiet splash" .
After rebooting i see this message:
```

Begin : Loading essential drivers... ...
Done.
Begin : Running /scripts/init_premount
Done.
Begin : Mounting root file system... ...
Begin : Running /scripts/local-top...
Done
Begin : Running /scripts/local-premount ...
Done.
[4.349366] EXT4-fs (sda 5): mounted filesystem with ordered data mode
Begin : Running /scripts/local-bottom ...
Done.
Done.
Begin : Running /scripts/init_bottom ...
Done.

```
And then nothing happens.

Before this problem started I upgraded few packages (i.e. eclipse) and i have to shut down update manager. The synaptic said that i have to type "sudo dpkg --configure -a" command. And after this everything seemed to be all aright.

---

