---
title: "configuration files"
date: 2010-12-04
forum: General Help
---

### Post by owiknowi on 2010-12-04
In which configuration files can I manually set the default screen brightness?

---

### Post by DeMus on 2010-12-04
> **owiknowi said:**
> In which configuration files can I manually set the default screen brightness?

Which graphic card do you have?

---

### Post by wojox on 2010-12-04
Open gconf-editor (Alt+F2) and go to:

apps > gnome-power-manager > backlight

and change the setting there.

---

### Post by owiknowi on 2010-12-05
> **DeMus said:**
> Which graphic card do you have?

Thanks for your reply.
It's an integrated Intel GMA something.
The notebook is a Compal NTUC0, one of the rare species I could buy without a MS license.
The problem with the Fn+Fx keys not working may be due to the very basic/poor BIOS?

---

### Post by owiknowi on 2010-12-05
> **wojox said:**
> Open gconf-editor (Alt+F2) and go to:

apps > gnome-power-manager > backlight

and change the setting there.

Thanks for your reply.
Already bin there but nothing happens.

During a session only the following command works:
setpci -s 00:02.0 F4.B=20
After a reboot however the screen is blinding, again.

So I'm looking for the configuration files to manually edit them.

BTW: Fn+ volume keys neither work.

---

### Post by SeijiSensei on 2010-12-05
Use your favorite editor with sudo and add the "setpci" command to /etc/rc.local.  It's the last file executed during the boot process.  Make sure the command is placed above "exit 0" at the bottom of the file.

---

### Post by owiknowi on 2010-12-05
> **SeijiSensei said:**
> Use your favorite editor with sudo and add the "setpci" command to /etc/rc.local.  It's the last file executed during the boot process.  Make sure the command is placed above "exit 0" at the bottom of the file.

Thank you very much! It works!
Just before the desktop appears brightness now goes to the preferred value.

---

