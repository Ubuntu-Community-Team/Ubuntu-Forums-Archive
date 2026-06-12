---
title: "What are the memory test modules in boot menu?"
date: 2011-09-18
forum: General Help
---

### Post by deepaknet on 2011-09-18
Dear Ubuntu Team,

I see two x86 memory test modules in the boot menu along with the operating systems being listed. What are these options for? How to remove them or are they necessary?

---

### Post by drs305 on 2011-09-18
They extensively test your system's memory and are not necessary. The [_wikipedia_]("http://en.wikipedia.org/wiki/Memtest86") page is fairly good at explaining it.

If you don't want to see the entries, you can disable the script with the following command:
```
sudo chmod -x /etc/grub.d/20_memtest86+
```

Or tweak the Grub settings using Grub Customizer. Click the 'Customizer' link in my signature line.

---

