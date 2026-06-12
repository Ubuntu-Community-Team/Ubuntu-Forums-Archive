---
title: "HDD Overheating"
date: 2011-09-21
forum: General Help
---

### Post by GuitarRocker2562 on 2011-09-21
I'm using ubuntu 11.04 on a Dell netbook and if I leave ubutnu on fora few hours my hard drive always overheats (60c or hotter) which is very bad. Its worth noting I almost always keep the netbook plugged in and it seems as if my hard drive never spins down. I don't have this problem in Windows. How can I prevent this issue?

---

### Post by scarleo on 2011-09-21
First you need to find out what is using the harddrive. You can see disk activity with iotop, install it if you don't have it. run it and check what applications are writing to disk. You can also try powertop to find causes to disk wakeups.

---

### Post by An Sanct on 2011-09-21
Swap can also cause disk wake up (or non-sleep), Do you have the appropriate amount or RAM to avoid swap?

---

### Post by mcduck on 2011-09-21
...of course it should be mentioned that the hard drive is made to be able to run continuously, so if it's overheating that's definitely a hardware problem related either to bad design of the computer and it's cooling, or simply the computer having collected too much dust that is preventing proper airflow.

Every computer component you can find is supposed to be able to run continuously under full load

Of course that doesn't mean that spinning down the drive wouldn't be usefully on a notebook/netbook. It's a nice way to save some battery life. But it definitely shouldn't be necessary for protecting your drive from failing. (Personally, I'd return any hardware that can't handle continuous load to the seller as a faulty product.)

---

### Post by Jouke74 on 2011-09-21
Is your computer fan (CPU) working ok? Does it spin up when you're doing lot's of stuff? This is important because usually the fan does not only cools down the CPU, but also other hardware in netbooks. It is very uncommon that the HD needs to spin down to cool down. 

Try the following kernel line in grub:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux" 
And see if it makes a difference. 

On the hardware side: check if all vents are clean and you have no pile of dust inside the machine which blocks cooling to HD. However, given that windows works I assume that the temperature sensors are read incorrectly and the cooling is insufficient.

Also under gnome-power-management you can set the harddisk to spin down when on AC power. I think normally this is not checked (when not on battery).

---

### Post by TenPlus1 on 2011-09-21
go into terminal and type:

   sudo gedit /etc/sysctl.conf

and at the very end of the document add this line:

   vm.swappiness = 20

now save and reboot, this will force Ubuntu to use your physical memory before going near the swap partition...

---

### Post by mcduck on 2011-09-21
> **TenPlus1 said:**
> go into terminal and type:

   sudo gedit /etc/sysctl.conf

and at the very end of the document add this line:

   vm.swappiness = 20

now save and reboot, this will force Ubuntu to use your physical memory before going near the swap partition...

The kernel memory management is not quite that simple, swappiness is just one of the things the kernel considers when deciding between keeping something in RAM, swapping it or dropping it completely. Even setting swappiness to 0 would not stop the kernel from swapping when it needs to do so, it only makes it less likely to favor swapping over dropping some cached data.

Sure, setting swappiness to lower value can be useful for allowing the hard drive to spend more time sleeping, once again a great feature for maximizing battery life, but I'd still say the big question here is why the drive overheats when running, not how to stop it from running. :)

---

### Post by GuitarRocker2562 on 2011-09-21
While I only have 1GB of ram my swap partition is almost never used. The disk light on my netbook is rarely on but the hard drive seems to never spin down. This netbook doesn't have a fan (other than CPU) and while it can get hot under windows when using the disk a lot it gets a lot hotter under ubuntu.

---

### Post by GuitarRocker2562 on 2011-09-21
After running iotop for bout a half hour I see that I have low disk usage however about every 5 seconds a couplers different things will quickly write to the disk. Is there a way golly my usage so I can see what's using it exactly? Is there a way to make sure that programs hold off on writing to the disk until about once a minute.

---

### Post by Mark Phelps on 2011-09-21
Your laptop hard drive shares the same case as your other components.  If your CPU is running HOT (a likely scenario if, unlike with Win7, Ubuntu is NOT powering down the CPU when the PC is idle), then it will heat up all the other components in the case as well.

If you have access to SMART data that shows HDD temps, then monitor the temp from when you first turn on the laptop (from being cold) to when it starts to heat up.

As folks have said, hard drives are designed to run constantly, at a given speed, so it's more likely that something else is overheating the drive, than it's overheating itself.

---

