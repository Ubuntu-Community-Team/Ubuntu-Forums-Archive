---
title: "GRUB gone?"
date: 2006-05-10
forum: General Help
---

### Post by Prudentissimus on 2006-05-10
Hi,


       I installed WinXP, and I cannot see the GRUB Menu now! Please help!


Thanks!

](*,)

---

### Post by xXx 0wn3d xXx on 2006-05-10
[QUOTE=Prudentissimus]Hi,


       I installed WinXP, and I cannot see the GRUB Menu now! Please help!


Thanks!

](*,)[/QUOTE]
This is normal. Windows installs it's own bootloader that only loads windows. Try booting into a windows recovery prompt and type:
> fixmbr
Then everything should be ok.

---

### Post by Sutekh on 2006-05-10
Windows XP is pretty hostile to poor GRUB.

You should read this link to get GRUB back

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Prudentissimus on 2006-05-10
Will "fixmbr" destroy my Windows XP boot, if it doesn't fix the Linux GRUB?

---

### Post by Sutekh on 2006-05-10
No, fixmbr *re-installs* the Windows bootloader on the MBR, wiping out GRUB.  This is basically what installing Windows after Ubuntu does.

I don't know how using the Windows bootloader can work with booting Ubuntu.  Best bet is the recovery link on the wiki.

---

