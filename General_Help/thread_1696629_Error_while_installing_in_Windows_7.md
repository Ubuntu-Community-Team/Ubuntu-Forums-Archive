---
title: "Error while installing in Windows 7"
date: 2011-02-27
forum: General Help
---

### Post by Panaxo on 2011-02-27
First thing i want to say, i´m not very good in English, becouse im chilean, so, if i have too many gramatical errors, please let me know...

Okay, while im finishing installing Ubuntu 10.10 in Windows 7, an error pop out an says:

---------------------------
Ubuntu Instalador
---------------------------
Ocurrió un  error:

Error executing command
>>command=C:\windows\System32\bcdedit.exe /set {f972d088-42bd-11e0-88bb-002454998f62} device partition=U:
>>retval=1
>>stderr=Error al establecer los datos del elemento.

Solicitud no compatible.


>>stdout=

Para más información vea el archivo de registro: c:\users\panaxo\appdata\local\temp\wubi-10.10-rev197.log

Sorry, it is in spanish, but i dont know how i can traduce it...
I tried to reinstall, but the same thing still happening.
I tried to install it in a partition of 40 gb, but while ubuntu let me choose the disk, i dont see it in the list, all i see are partition of differents capacitys...
If you want more information to help me, Mp me...

PD: Im installing Ubuntu from a Usb Disk.

---

### Post by Mark Phelps on 2011-02-28
Your system is trying to edit the BCD file to add an entry for Ubuntu -- and is failing in the process. Sometimes that error means that the installer is unable to gain proper access to the BCD file to do the editing.

This also happens with some Windows apps, and in those cases, the error was fixed by booting from the Windows install DVD and running Startup Repair.

If you don't have such a CD, then go into Windows 7, use the Backup feature to create and burn a Win7 Repair CD.  Then, boot from that and run Startup Repair. In many cases, it will find and fix the error in one pass.  But in some cases, it takes three passes.

If you fix it and you still get the error, you will need to look at the referenced wubi ...log file to see the error details.

---

### Post by bcbc on 2011-02-28
> **Panaxo said:**
> First thing i want to say, i´m not very good in English, becouse im chilean, so, if i have too many gramatical errors, please let me know...

Okay, while im finishing installing Ubuntu 10.10 in Windows 7, an error pop out an says:

---------------------------
Ubuntu Instalador
---------------------------
Ocurrió un  error:

Error executing command
>>command=C:\windows\System32\bcdedit.exe /set {f972d088-42bd-11e0-88bb-002454998f62} device partition=U:
>>retval=1
>>stderr=Error al establecer los datos del elemento.

Solicitud no compatible.


>>stdout=

Para más información vea el archivo de registro: c:\users\panaxo\appdata\local\temp\wubi-10.10-rev197.log

Sorry, it is in spanish, but i dont know how i can traduce it...
I tried to reinstall, but the same thing still happening.
I tried to install it in a partition of 40 gb, but while ubuntu let me choose the disk, i dont see it in the list, all i see are partition of differents capacitys...
If you want more information to help me, Mp me...

PD: Im installing Ubuntu from a Usb Disk.
U: is almost certainly a dynamic drive. You cannot install Ubuntu to a dynamic drive (either wubi or normal).

---

### Post by muquang on 2011-09-11
To fix this error, you must convert hard disk from dynamic disk to basic disk. Use EASEUS Partition Master Home Edition to convert(free soft + convert with no lost your data)

---

