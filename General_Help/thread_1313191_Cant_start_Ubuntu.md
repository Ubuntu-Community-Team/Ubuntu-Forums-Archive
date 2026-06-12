---
title: "Cant start Ubuntu"
date: 2009-11-03
forum: General Help
---

### Post by Defiant Rat on 2009-11-03
I changed some of the boot settings (resolution etc.) using startup-manager (in the software centre), and now when i try to start ubuntu i just get a black screen. Grub seems to load fine, so i can still boot windows, but when i select ubuntu it just goes to a black screen :(. Is there a way to reset these settings using the installation CD (or any other way) back to default, or am i going to have to do a fresh install :???:.

Ubuntu 9.10, 64 bit

Thanks

---

### Post by drs305 on 2009-11-03
> **Defiant Rat said:**
> I changed some of the boot settings (resolution etc.) using startup-manager (in the software centre), and now when i try to start ubuntu i just get a black screen. Grub seems to load fine, so i can still boot windows, but when i select ubuntu it just goes to a black screen :(. Is there a way to reset these settings using the installation CD (or any other way) back to default, or am i going to have to do a fresh install :???:.

Ubuntu 9.10, 64 bit

Thanks

Defiant Rat,

Are you using Grub 2? If you used StartUp-Manager to change the resolutions it may have borked it up. If you get the Grub 2 menu, highlight the entry you want, then press "e". It will display the lines for that entry. Look on the linux line and see if it added "vga=xxx" or something to that effect. If so, use the cursors and delete key to remove that entry. 

If there isn't a "vga=" entry, look through the lines and see if anything else looks resolution-related and remove it. 

These changes are not permanent. They only affect the current boot, so if you can get in you will need to edit your files. probably /etc/default/grub.

If you need to go deeper, refer to the GRUB2 link in my signature line for other CLI options or instructions on how to reinstall G2.

---

### Post by Defiant Rat on 2009-11-04
> **drs305 said:**
> Defiant Rat,

Are you using Grub 2? If you used StartUp-Manager to change the resolutions it may have borked it up. If you get the Grub 2 menu, highlight the entry you want, then press "e". It will display the lines for that entry. Look on the linux line and see if it added "vga=xxx" or something to that effect. If so, use the cursors and delete key to remove that entry. 

If there isn't a "vga=" entry, look through the lines and see if anything else looks resolution-related and remove it. 

These changes are not permanent. They only affect the current boot, so if you can get in you will need to edit your files. probably /etc/default/grub.

If you need to go deeper, refer to the GRUB2 link in my signature line for other CLI options or instructions on how to reinstall G2.

Thanks for that, im in, now i just need to find + edit the file.

Cheers :D

---

### Post by drs305 on 2009-11-04
> **Defiant Rat said:**
> Thanks for that, im in, now i just need to find + edit the file.

Cheers :D

The file you need to edit should be /etc/default/grub:
```

gksu gedit /etc/default/grub

```

Look for either 
GRUB_CMDLINE_LINUX_DEFAULT=
GRUB_CMDLINE_LINUX=""

One of them probably contains the line you had to edit during your successful boot. It may be the "vga=" entry. Whatever you did to get it to boot, do the same on the line above.

Save the file, then run:
```
sudo update-grub
```
and you should be set.

---

### Post by Defiant Rat on 2009-11-04
Worked perfectly, thanks a lot :D

---

