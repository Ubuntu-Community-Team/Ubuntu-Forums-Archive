---
title: "&quot;Add Printer&quot; missing when running system-config-printer"
date: 2010-08-01
forum: General Help
---

### Post by peter27 on 2010-08-01
Hi,

I want to add my printer to ubuntu 10.04. When I run the system-config-printer (System->Administration->Printing) I can't choose the "Add" in the menu bar (ctrl+n does not work either). Any ideas ?

Best Regards
Peter27

---

### Post by fragos on 2010-08-02
One reason for not adding is because the printer can't be seen. I had a printer disappear from Ubuntu's perspective. The solution was to unplug and then plug back in the USB cable for the printer. This isn't the first time I've had this happen with a USB device.

---

### Post by peter27 on 2010-08-06
My printer is a network printer.

---

### Post by peter27 on 2010-08-06
I found a solution. When i write

```

sudo /etc/init.d/cups restart

```

the "add new" icon gets visible and my printer is found.

Thanks for your help fragos.

---

