---
title: "Error when tring to uninstall (in wubi, to reinstall ubuntu)"
date: 2010-02-18
forum: General Help
---

### Post by rustynathan on 2010-02-18
So every time I manually uninstall, then reinstall with wubi. It doesn't show up in the bootloader. So, when I used wubi to uninstall, I get an error. It's too long to copy so I took a pic.[IMG]http://img138.imageshack.us/img138/9427/17171628.png[/IMG]

---

### Post by meierfra. on 2010-02-20
> So every time I manually uninstall, then reinstall with wubi. 

Why do you keep reinstalling Wubi?

> doesn't show up in the bootloader. 
If that is the only problem, you should be able to manually add Wubi to the Windows boot loader (or use EasyBCD).  Asked for help, if you would like to try that.


> So, when I used wubi to uninstall, I get an error. 

The Wubi un-installer   tries to delete the Wubi entry from the Windows boot loader, but since Wubi never got added to the Windows boot loader, you get  a "file missing" message.

---

### Post by thecliff on 2010-02-20
There is always booting and installing from disc/usb drive

---

