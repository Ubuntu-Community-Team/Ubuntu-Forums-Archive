---
title: "Cannot boot into Ubuntu"
date: 2010-11-28
forum: General Help
---

### Post by Vatteck on 2010-11-28
I'm using. Ubuntu 10.10.
After updating programs, and restarting, there's an error along the lines of "terminal_output missing" and then the computer restarts. How can I fix this?
I'm generally a beginner with Linux, so if you **do** help, please try to be simple.

---

### Post by wilee-nilee on 2010-11-28
from a live Ubuntu cd or thumb, to make this easiest lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by Vatteck on 2010-11-28
I'm in the process of creating a Live CD, but i looked at the error more carefully, and it said "**No wubildr**"
Any ideas?

---

### Post by Vatteck on 2010-11-28
**Anyone?**

---

### Post by miegiel on 2010-11-28
> **Vatteck said:**
> I'm in the process of creating a Live CD, but i looked at the error more carefully, and it said "**No wubildr**"
Any ideas?

I never tried wubi, but I've read that updates often break wubi. In general it's better to make some free space (20GB at least) for a separate linux partition and install ubuntu the "normal" way.

---

### Post by Vatteck on 2010-11-29
> **miegiel said:**
> I never tried wubi, but I've read that updates often break wubi. In general it's better to make some free space (20GB at least) for a separate linux partition and install ubuntu the "normal" way.

I just made a CD and tried, and the window list and workspace switcher panels weren't there, corrupted or something.. and when i tried to install it, there wasn't the option to install it alongside another OS, and i didn't know what the hell to do at the advanced part.

---

### Post by miegiel on 2010-11-29
> **Vatteck said:**
> I just made a CD and tried, and the window list and workspace switcher panels weren't there, corrupted or something.. and when i tried to install it, there wasn't the option to install it alongside another OS, and i didn't know what the hell to do at the advanced part.

When you boot the CD select "try ubuntu" instead of "install ubuntu". Once ubuntu has booted find the gParted program. With that you can resize your windows partition to make some space.

**But** before resizing you should always defragment your disks (in windows). This makes the whole process a lot safer, almost safe even.

**Still**, make sure you backup anything on the disk you would never want to loose

---

### Post by Vatteck on 2010-11-29
> **miegiel said:**
> When you boot the CD select "try ubuntu" instead of "install ubuntu". Once ubuntu has booted find the gParted program. With that you can resize your windows partition to make some space.

**But** before resizing you should always defragment your disks (in windows). This makes the whole process a lot safer, almost safe even.

**Still**, make sure you backup anything on the disk you would never want to loose

When i booted from the CD, it just went to the desktop, and there was a file on it called "Install Ubuntu 10.10"

---

### Post by miegiel on 2010-11-29
> **Vatteck said:**
> When i booted from the CD, it just went to the desktop, and there was a file on it called "Install Ubuntu 10.10"

Ignore that "Install Ubuntu 10.10" file for now. gParted is somewhere in the menus, in system I think.

---

