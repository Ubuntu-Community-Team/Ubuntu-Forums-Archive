---
title: "USB devices don't auto-mount anymore"
date: 2009-10-03
forum: General Help
---

### Post by DeMus on 2009-10-03
Since a day or two I notice that my external USB hard disk and my USB stick don't auto-mount when I plug them in.
They don't appear in Nautilus. The device is visible when I type
```
lsusb
```
in a terminal.
What could have happened? It used to work. Where do I have to look, what do I have to do to get this fixed?

Thanks.

---

### Post by DeMus on 2009-10-03
Come on people, you are all using USB devices. Help me out here, please.

---

### Post by Kapitän Rotbart on 2009-10-03
Solution on [this thread]("http://ubuntuforums.org/showthread.php?t=1134501&page=2") seemed to work for some people. They suggest adding **usb_storage** to etc/modules.

Have you checked your fstab (etc/fstab)? I haven't had any trouble mounting usb automatically in Ubuntu myself except for in ubuntu-eee (8.04 Hardy) where I had to toggle comments for the entry on mounting usb, so I guess that's the best I can recommend.

---

### Post by DeMus on 2009-10-03
> **Kapitän Rotbart said:**
> Solution on [this thread]("http://ubuntuforums.org/showthread.php?t=1134501&page=2") seemed to work for some people. They suggest adding **usb_storage** to etc/modules.

Have you checked your fstab (etc/fstab)? I haven't had any trouble mounting usb automatically in Ubuntu myself except for in ubuntu-eee (8.04 Hardy) where I had to toggle comments for the entry on mounting usb, so I guess that's the best I can recommend.

Thank you so very much. It's working again. I just don't understand what happened, because it always worked, until some days ago. And I surely did not remove that one line form the /etc/modules file.
Well, doesn't matter, it's working again. Thank you very much.

---

