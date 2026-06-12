---
title: "USB on Wine?"
date: 2011-05-22
forum: General Help
---

### Post by joelstitch on 2011-05-22
So I have been looking around on how to get Wine to read USB devices but all the information I have found is old and haven't worked for me. I am trying to do some stuff to my Blackberry with a windows program that I have install using Wine but its not detecting the device. Anybody knows how to get this to work?

---

### Post by linuxinstalledfromhdd on 2011-05-22
Is it something you need all the time? I would suggest, why use wine for this when you can use Virtualbox that does support USB?  Install virtualbox in your Ubuntu instead. Run whatever OS you need natively from there and you will have USB accessibility.  That way you don't have to sacrifice anything and still have Ubuntu as your main OS. That's what I do.

---

### Post by joelstitch on 2011-05-22
I use virtualbox but I would prefer not having to go to all the process of starting a new OS and taking up RAM if I can just do it with Wine.

---

### Post by linuxinstalledfromhdd on 2011-05-22
[http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)

---

### Post by joelstitch on 2011-05-22
> **linuxinstalledfromhdd said:**
> [http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)

So I did most of the directions but got stuck at the end where it says:

> For using native USB driver should copy HKLM\System\[CurrentControlSet]("http://wiki.winehq.org/CurrentControlSet")\Enum\USB\Vid_<vid>&Pid_<pid> and HKLM\System\[CurrentControlSet]("http://wiki.winehq.org/CurrentControlSet")\Services\<driver_name>  from Windows registry. Where <vid> means vendor id, <pid>  means product id. In Linux one may run 

lsusb -v 

to get detailed information about connected USB devices and to check vid and pid. 

Example of data taken from Windows registry: 

[B][HKEY_LOCAL_MACHINE\System\CurrentControlSet\Enum\USB\Vid_073d&Pid_0025\5&6d75465&0&1] "ClassGUID"="{36FC9E60-C465-11CF-8056-444553540000}" "HardwareID"=hex(7):55,53,42,5c,56,69,64,5f,30,37,33,64,26,50,69,64,5f,30,30,32,\   35,26,52,65,76,5f,30,32,30,30,00,55,53,42,5c,56,69,64,5f,30,37,33,64,26,50,\   69,64,5f,30,30,32,35,00,00 "Service"="DRIVERNAME"  

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DRIVERNAME] "ErrorControl"=dword:00000001 "ImagePath"="system32\\drivers\\DRIVERNAME.sys" "Start"=dword:00000003 "Type"=dword:00000001 When  editing registry in the example above you could also write  "HardwareID"="USB\\VID_073d&Pid_0025\\..." The driver should be put  in the directory specified by HKLM\System\[/B] **[CurrentControlSet]("http://wiki.winehq.org/CurrentControlSet")\Services\<driver_name>\[ImagePath]("http://wiki.winehq.org/ImagePath"). Also you need to have permissions to read/write to USB device.** 

My Vendor ID is 0x1d6b Linux Foundation
My Product ID is 0x0002 2.0 root hub

But I dont exactly get how to transfer the registry...

---

### Post by linuxinstalledfromhdd on 2011-05-22
bump

---

### Post by joelstitch on 2011-05-22
I'm guessing I have to use Git but I'm not sure how to copy the registry ...

---

### Post by joelstitch on 2011-05-27
So I figures out how to copy the registry but I still can't get it to work. I am trying to use the [Blackberry Master Control Program]("http://crackberry.com/blackberry-master-control-program-out-beta"), I plug my phone to the computer and open the program but the program doesn't detect the phone.

---

