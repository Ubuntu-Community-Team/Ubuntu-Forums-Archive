---
title: "How to include a manufacturer's NIC driver in the linux kernel?"
date: 2012-06-23
forum: General Help
---

### Post by tokyo-joe on 2012-06-23
I have been experiencing a NIC related issue, so I installed a driver from the manufacturer and blacklisted the original driver included in the kernel.

   System: Ubuntu 12.04 LTS 64bit
   Motherboard: ASUS P5B-E Plus
   NIC Chipset: Marvell Yukon 88E8056
   Original Driver in the kernel: sky2
   New Driver from the Manufacturer: [http://www.marvell.com/support/downloads/driverSearchResults.do;jsessionid=1mTtPmbGq7NZ7qJxjZZVp0GChgTMszK1WjBs1hz91ymh1p11GjnB!2084298837#](http://www.marvell.com/support/downloads/driverSearchResults.do;jsessionid=1mTtPmbGq7NZ7qJxjZZVp0GChgTMszK1WjBs1hz91ymh1p11GjnB!2084298837#)

However, after the installation, the original driver (sky2) is still loaded at boot. How can I avoid sky2 driver loaded on boot?

I blacklisted the sky2 driver by adding the following line in  /etc/modprobe.d/blacklist.
    blacklist sky2

---

### Post by wildmanne39 on 2012-06-23
Hi, in 12.04 blacklist.conf is the name of the file, this is how I do it.
```
echo "blacklist nameofdriver" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by tokyo-joe on 2012-06-28
As posted in the thread below, I am trying to load the Marvel Yukon NIC driver as the default driver.
[http://ubuntuforums.org/showthread.php?t=2009034](http://ubuntuforums.org/showthread.php?t=2009034)

I have tried the following things.
[LIST]
Blacklisting kernel's driver (sky2) in /etc/modprobe.d/blacklist.conf
Removing sky2 driver by "sudo rmprobe sky2"
[/LIST] 

Once those are done, the newly installed driver (sk98lin) starts working. However, after the boot, the system load the kernel's driver (sky2) again.

So I tried to perform the install script in the Marvel's driver package again, then I found that the script fails to identify the linux kernel.

What is missing to let the install script identify the linux kernel and include the driver into the kernel?

FYI, the system is Ubuntu 12.04 LTS 64bit. The kernel is up-to-date now.

---

### Post by cariboo on 2012-06-29
Please don't create multiple threads on the same subject, J have merged your two threads.

---

### Post by wildmanne39 on 2012-06-29
Hi, if you ran the command in my first post then this one should get it to load the driver on boot.
```
sudo su 
echo sk98lin >> /etc/modules 
exit

```
Thanks

---

### Post by AntiKris on 2012-08-10
Just curious if this was ever resolved.  I'm having the same difficulty.  Followed all instructions, blacklisted sky2, and it's still there.  Annoyingly, I ran the install script from Marvell which is supposed to remove the sky2 driver, and that didn't work either.

---

### Post by chiefwilson on 2012-10-31
> **Wild Man said:**
> Hi, if you ran the command in my first post then this one should get it to load the driver on boot.
```
sudo su 
echo sk98lin >> /etc/modules 
exit

```
Thanks

I followed all instructions, but no luck yet. This sky2 driver issue is giving me a headache since I'm running a headless server :(

---

