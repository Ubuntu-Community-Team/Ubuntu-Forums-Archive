---
title: "Removing grub"
date: 2010-02-06
forum: General Help
---

### Post by petersohn on 2010-02-06
I tried to install Ubuntu on an external drive, but it doesn't boot, but it installed GRUB on my main HD, and now I can't even boot Windows. I only get a "grub rescue" prompt. I need to remove GRUB. How to do it?

---

### Post by Techsnap on 2010-02-06
Insert your Windows CD.

Windows 2K/XP

Press R to repair the installation, then type fixmbr at the command prompt.

Vista/7:

Insert the disc and Click Repair>Command Prompt, enter the following commands:

```
bootrec.exe /fixboot
```

and:

```
bootrec.exe /fixmbr
```

---

### Post by petersohn on 2010-02-06
Is there no way to remove GRUB from Linux?

---

### Post by Techsnap on 2010-02-06
I don't know much about GRUB (I use LILO) do you not have any Windows installation media available?

---

### Post by petersohn on 2010-02-06
It is a corporate laptop with Win Vista and I only have XP and Win 7 install CD at home. The XP CD says it can't see my disk. I'm still trying the Win 7 CD.

---

### Post by petersohn on 2010-02-06
The Win 7 CD helped me. Thanks.

---

### Post by Techsnap on 2010-02-06
You're welcome.

---

