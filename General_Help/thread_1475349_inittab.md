---
title: "inittab"
date: 2010-05-06
forum: General Help
---

### Post by nsblenin on 2010-05-06
Hello. I just want to start my ubuntu 10.04 i terminal mode without gnome or kde. I saw that in previous versions there was a file called /etc/inittab that let you select the mode to start ubuntu. Why I don't have this file and how can i start in "3" mode. Thanks

---

### Post by jbrown96 on 2010-05-06
[edit] Do what kerry_s says below

---

### Post by kerry_s on 2010-05-06
> **nsblenin said:**
> Hello. I just want to start my ubuntu 10.04 i terminal mode without gnome or kde. I saw that in previous versions there was a file called /etc/inittab that let you select the mode to start ubuntu. Why I don't have this file and how can i start in "3" mode. Thanks

ubuntu now uses upstart.

i think, what you can do is is edit /etc/default/grub & add the "3"

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **3**"
```

make sure to run "**sudo update-grub**" after editing.

---

