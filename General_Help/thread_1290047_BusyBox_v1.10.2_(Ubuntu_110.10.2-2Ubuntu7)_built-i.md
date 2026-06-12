---
title: "BusyBox v1.10.2 (Ubuntu 1:10.10.2-2Ubuntu7) built-in shell (ash)"
date: 2009-10-13
forum: General Help
---

### Post by Rodart on 2009-10-13
Ok, so my friend manage to activate his CnC , but this shows up now:confused: :
[http://img98.imageshack.us/img98/5261/dsc09012.jpg](http://img98.imageshack.us/img98/5261/dsc09012.jpg)
this shows up after he chooses Ubuntu boot option.

Thanks.
Rodart.

---

### Post by P4man on 2009-10-13
Looks like an install went bad. Is it a new install or booting from live cd/usb ? Check the install medium (cd or usb stick) for defects: in the live cd menu you have the option "check this cd for errors" or similar.

---

### Post by MaTiAsMaX on 2009-10-13
sorry. I am the friend of Rodart. install it with wubi.

any solution? thanks

---

### Post by Rodart on 2009-10-13
> **P4man said:**
> Looks like an install went bad. Is it a new install or booting from live cd/usb ? Check the install medium (cd or usb stick) for defects: in the live cd menu you have the option "check this cd for errors" or similar.
 
well he downloaded Ubuntu 9.04 and then he installed it with wubi , when he enters ubuntu from the booting options at startup that comes up.
Thanks.

Rodart

---

### Post by jmszr on 2009-10-13
Rodart/MaTiAsMaX,

Wubi installs Ubuntu into a Windows folder - usually a NTFS type of file system, this file system has a known reaction of being unstable in other operating systems like Ubuntu when a hard shutdown happens.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties. Select the "Tools" tab and click "check now" under error checking (with Vista you might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down  by using the start menu (Do Not hard reboot) and  try using Ubuntu now. ( From Ago)
                  
You can also accomplish the immediate previous tip by running chkdsk/f  in Windows and then shutting down properly.

Hope that helps.

---

