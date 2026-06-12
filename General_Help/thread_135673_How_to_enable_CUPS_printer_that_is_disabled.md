---
title: "How to enable CUPS printer that is disabled"
date: 2006-02-24
forum: General Help
---

### Post by jfdill_2 on 2006-02-24
Using the gnome-cups-manager to re-enable printers has not worked for me, for example after the printer has some error and becomes disabled, even when I run it with "sudo gnome-cups-manager".

As a workaround, I found that this works:  Browse to [http://localhost:631/printers/](http://localhost:631/printers/) then click on "Start printer" for the printer that is disabled.

---

### Post by bosonflux on 2006-02-24
You can also do /etc/init.d/cupsys restart. Besure to be root in a terminal.

---

### Post by jfdill_2 on 2006-02-24
[QUOTE=bosonflux]You can also do /etc/init.d/cupsys restart. Besure to be root in a terminal.[/QUOTE]
I did that, but the printer was still "disabled" after I restarted CUPS.

---

