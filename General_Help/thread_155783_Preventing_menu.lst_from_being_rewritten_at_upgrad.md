---
title: "Preventing menu.lst from being rewritten at upgrade"
date: 2006-04-05
forum: General Help
---

### Post by dengar on 2006-04-05
I dual boot windows and ubuntu using grub (whichever version is standard included with Breezy Badger 5.10)

I know there use to be a gui that was accesible under the administrator toolbar to set what grub options there were. I don't know what happened to that so I've been editing menu.lst in the grub folder manually.

Unfortunately many times that I install updates (which ubuntu helpfully reminds me of) a new kernel is installed and the grub menu.lst is rewritten (at least that's why I think its rewritten at updates) is there a way to stop this from happening, or at the least force the rewrite to not alter the portion of menu.lst that has my dual boot options

---

### Post by dcstar on 2006-04-05
[QUOTE=dengar]I dual boot windows and ubuntu using grub (whichever version is standard included with Breezy Badger 5.10)

I know there use to be a gui that was accesible under the administrator toolbar to set what grub options there were. I don't know what happened to that so I've been editing menu.lst in the grub folder manually.

Unfortunately many times that I install updates (which ubuntu helpfully reminds me of) a new kernel is installed and the grub menu.lst is rewritten (at least that's why I think its rewritten at updates) is there a way to stop this from happening, or at the least force the rewrite to not alter the portion of menu.lst that has my dual boot options[/QUOTE]
If you look at the menu.lst file it specifically has a place at the end which doesn't get altered during updates.
```
### BEGIN AUTOMAGIC KERNELS LIST
## [B]lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below[/B]
.....
### END DEBIAN AUTOMAGIC KERNELS LIST
```
If you have not placed your dual-boot code there then it will not survive an update.

---

