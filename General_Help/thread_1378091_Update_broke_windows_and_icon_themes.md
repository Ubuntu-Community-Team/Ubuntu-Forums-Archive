---
title: "Update broke windows and icon themes"
date: 2010-01-11
forum: General Help
---

### Post by lian1238 on 2010-01-11
Hi all,

I just did install the updates as they showed up with the Update manager, and now the themes are "broken." On startup, all windows are themed with the Redmond theme. When I open the Appearance dialog, some windows' theme come back. But nautilus still uses the Redmond theme (I'm not running it as root either). The icon theme is totally not taking effect. It's using the ugly gray icons regardless of what I have chosen.

This all happened right after the latest update on Karmic, and after I've reinstalled my NVidia driver which breaks after every kernel update. I think it was a kernel update because the number of lines at the grub menu seemed to have increased.

Thanks in advance for any help and advice.

---

### Post by lian1238 on 2010-01-11
I just noticed something else. If I run nautilus as root, the control theme is applied.

---

### Post by garvinrick4 on 2010-01-11
If you got another kernel in your boot choices you got a new kernel. Choose the kernel that is
the one you were using (below the new kernel in boot choices). You will be back to the way
it was. If it works you no it is the new kernel and go from there.

---

