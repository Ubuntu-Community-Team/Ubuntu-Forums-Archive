---
title: "How can I uninstall v. 11.04?"
date: 2011-05-01
forum: General Help
---

### Post by steveontario on 2011-05-01
Well, the upgrade from 10.10 to 11.04 has proved to be an unmitigated disaster for my netbook. I have no menus! Nothing at the top (i.e. the usual Gnome desktop with "Browse and run installed applications," "Applications," "Places," "System") and no Unity buttons available wherever I put the cursor.

Plus, when the system goes to sleep and I press the power button to revive it, it reboots!

I don't understand how v. 11.04 is an improvement over v. 10.10.

Does anyone know how I can uninstall v 11.04 -- bearing in mind I have no menus -- so I can reinstall v. 10.10?

---

### Post by Megaptera on 2011-05-01
Can you boot in to a 10.10 live CD? Use Gparted to delete 11.04 & then reinstall 10.10?

---

### Post by steveontario on 2011-05-01
mega, thanks. My netbook doesn't have a cd player, so I'd have to reboot from a usb cd/dvd.

Could I remove it from Windows (I can boot it to Windows)? Then I could reinstall 10.10.

---

### Post by Megaptera on 2011-05-01
> **steveontario said:**
> mega, thanks. My netbook doesn't have a cd player, so I'd have to reboot from a usb cd/dvd.

Could I remove it from Windows (I can boot it to Windows)? Then I could reinstall 10.10.

No you can't remove from within Windows unless it's a Wubi install - is it Wubi by any chance?.
You'd have to use USB or usb cd/dvd as you suggested.

---

### Post by TeoBigusGeekus on 2011-05-01
> **Megaptera said:**
> No you can't remove from within Windows unless it's a Wubi install - is it Wubi by any chance?.
You'd have to use USB or usb cd/dvd as you suggested.

You can remove ubuntu from within windows if you go to Administrative Tools, find disk management and format your ubuntu partitions (which will be shown as unformatted in windows).

...but you don't have to do it. Just boot with the live usb and install 10.10 on top of Natty formatting the partitions.

---

