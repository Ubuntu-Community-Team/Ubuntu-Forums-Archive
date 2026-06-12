---
title: "Attach/Detach usb device remotely"
date: 2010-09-07
forum: General Help
---

### Post by alikthename on 2010-09-07
I have a usb wimax wireless adapter. Some times it stops responding to commands and I have to detach and attach it again phisically.
My question is:  is it possible to do equvalent operation remotely, over ssh like in case with mounting/unmounting filesystems?

---

### Post by mikewhatever on 2010-09-07
Unloading the module and then reloading might work.

sudo rmmod **modname**

sudo modprobe **modname**

Obviously, the modname is something specific to the adapter. In case you don't know the name, use the **lsmod** command to print out all currently loaded modules.

---

### Post by alikthename on 2010-09-07
> **mikewhatever said:**
> Unloading the module and then reloading might work.

sudo rmmod **modname**

sudo modprobe **modname**

Obviously, the modname is something specific to the adapter. In case you don't know the name, use the **lsmod** command to print out all currently loaded modules.

Thanks a lot. I'll try this solution when adapter will become unresponsive. For now I just tried to remove the module while modem was working ok and it did not allowed me to saying that the module is in use, and while the man of rmmod says that using rmmod -f is extremely dangerous I'll refuse to try it.

---

### Post by mikewhatever on 2010-09-07
In that case, you should probably bring down the interface first using the command below. The interface names are usually eth1, eth2, etc. You can find out the exact name by running **ifconfig**.

sudo ifconfig eth1 down

Then, reload the module and bring eth1 back up.

sudo ifconfig eth1 up

---

### Post by alikthename on 2010-09-08
> **mikewhatever said:**
> In that case, you should probably bring down the interface first using the command below. The interface names are usually eth1, eth2, etc. You can find out the exact name by running **ifconfig**.

sudo ifconfig eth1 down

Then, reload the module and bring eth1 back up.

sudo ifconfig eth1 up

Yeah, I thought about that.

---

### Post by alikthename on 2010-09-09
Well, today wimax adapter stopped respondig and I went on trying solutions. And have to say that it still does not allow me to disable the module saying its in use even after  making ifconfig wimax0 down.
The module I try to rmmod is tun. I found it via lshw.


 *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wimax0
       serial: 00:24:91:39:dc:f0
       size: 10MB/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes [COLOR="Red"]driver=tun[/COLOR] driverversion=1.6 duplex=full firmware=N/A link=yes multicast=yes port=twisted pair speed=10MB/s

Please point me where am I wrong

---

