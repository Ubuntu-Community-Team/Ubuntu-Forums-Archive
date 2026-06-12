---
title: "Put Ubuntu to sleep using terminal"
date: 2009-07-29
forum: General Help
---

### Post by ILMV on 2009-07-29
Hello all,

I have a server running the desktop version of 9.04, I have installed openssh onto it, and want to be able to send the box to sleep as I please, just to save a bit of power.

I don't think the shutdown command has an option to do so, so does anyone know how to maybe Ubuntu sleep via the terminal?

Thanks, Ben

---

### Post by philinux on 2009-07-29
Maybe this might help.

[http://ubuntuforums.org/showthread.php?t=813387](http://ubuntuforums.org/showthread.php?t=813387)

---

### Post by wojox on 2009-07-29
No, if you want to save power/resources uninstall the GUI. You may be able to suspend it with the GUI but I don't know how.

---

### Post by ILMV on 2009-07-29
> **philinux said:**
> Maybe this might help.

[http://ubuntuforums.org/showthread.php?t=813387](http://ubuntuforums.org/showthread.php?t=813387)

Thanks for that link, I tried most of them specified, but none of them appeared to work. By the way I am SSHing into my box, I should have made that clear.

The server hardware is a bit old now, are any of those commands hardware dependant?

Thanks

---

### Post by liquider on 2011-04-10
just solvin',

it's 
```
sudo /etc/acpi/sleep.sh force
```
from this thread: [http://ubuntuforums.org/showthread.php?t=591036](http://ubuntuforums.org/showthread.php?t=591036)

---

