---
title: "Help lost usb drive for netbook and cant access windows"
date: 2010-06-17
forum: General Help
---

### Post by armyknight2002 on 2010-06-17
I installed ubuntu's netbook version on a usb drive and i lost it and now i cant access windows i get...
 
error: no such device: 0022a70f-cd9c-45f9-bcac-0649d9bab967.
grub rescue>
 
now i am trying to access windows to reinstall everything and i dont know how keep this in mind when you help me 
 
i have a recovery disk for windows xp, i installed ubuntu from a cd to the usb drive that i lost now im stuck and i dont know what to do pleas help :cry:

---

### Post by wilee-nilee on 2010-06-17
Really you will have to get in with a thumb or cd/dvd reader in the end probably. If you can get either of these devices from a live cd run the script in my sig and post it in code tags.

You don't describe how you installed the netbook is it a wubi install. More information is needed other then the error.

If your able to get into the netbook then run the script from there you don't say if you can get into the Ubuntu part

---

### Post by C.S.Cameron on 2010-06-17
You should be able to boot your Windows install CD and start Recovery Console.

Once it is started type "fixmbr".

This has happened to me a few times when doing a full insstall to USB without disabling my internal drives.

---

### Post by wilee-nilee on 2010-06-17
> **C.S.Cameron said:**
> You should be able to boot your Windows install CD and start Recovery Console.

Once it is started type "fixmbr".

This has happened to me a few times when doing a full insstall to USB without disabling my internal drives.

I suspect that this is a grub in windows problem, this command only changes the mbr, and doesn't remove the grub in the windows partition if that is what has happened. I might be wrong here though. The script will tell us what is going on. And if this command is run there will no bootable OS to run the script without a Live cd or a thumb, leaving the user in a worse scenario, if Ubuntu boots now.

---

