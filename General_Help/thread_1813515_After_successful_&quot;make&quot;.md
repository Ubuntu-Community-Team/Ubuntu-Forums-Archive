---
title: "After successful &quot;make&quot;"
date: 2011-07-27
forum: General Help
---

### Post by ESimard on 2011-07-27
Hi, after a successfully "make" and "make install" installing a serial card I have the ports ttyD1 and ttyD2.  But after a reboot I have to run the "make install" again.  After the "make install"  how do I make the changes permanent?

Thanks in advance
_Ernie

---

### Post by Slim Odds on 2011-07-27
A little hint as to what you're "making" would be very helpful

---

### Post by ESimard on 2011-07-27
It was the MCS9865 drivers for a Moschip serial card.  After the make and make install, ports ttyD0 and ttyD1 are available and work correctly.  After a reboot the ttyD*'s are gone.  Reentering the make install puts them back.  It appears that something additional need to be entered to make the additional ports permanent, or perhaps I missed some step.  
_Ernie

---

### Post by Slim Odds on 2011-07-28
I would look at the make file to see what "make install" is doing.

My guess is that there is something that you need to add to the Ubuntu start-up scripts to do the same thing that "make install" is doing.

---

### Post by whitethorn on 2011-07-28
I'm guessing in the make install script, they're probably loading some sort of modules. Have you tried loading the modules after a reboot? Best bet would be to run 

```
lsmod
```

before and after a make install, whatever new modules are listed are the ones the install script is loading (another way would to just look into the script and look for the modprobe command).

Once you have the name of the modules being loaded, add them to the following file.  /etc/modules

```
sudo nano /etc/modules
```

then add the module names, one per line
> 
module1
module2
.
.
.


---

### Post by oldos2er on 2011-07-28
> **ESimard said:**
> Hi, after a successfully "make" and "make install" installing a serial card I have the ports ttyD1 and ttyD2.  But after a reboot I have to run the "make install" again.  After the "make install"  how do I make the changes permanent?


Try **sudo make install**

---

### Post by Wim Sturkenboom on 2011-07-28
> **oldos2er said:**
> Try **sudo make install**

*make install* without elevated privileges should not allow one to create something in /dev; I assume (I know it's dangerous) that that is where ttyD0 etc are.

Maybe you know something that I don't know ;)

---

### Post by oldos2er on 2011-07-28
Perhaps the OP was running *make install* from inside a root shell; ESimard can you clarify?

---

### Post by ESimard on 2011-07-28
Hi, I just ran it as sudo make install (then entered the password).

New strangeness:
I edited the makefile adding a -v to both modprob commands, reran sudo make install, no errors shown.  I added the two files to /etc/modules.  Checking with lsmod I see both files and the serial ports are present.  

Reboot: lsmod does not show the two files and of course the ports are not present.  So it appears that make install put the modules in place but they do not survive a reboot.

Makefile entries:

KDIR:=/lib/modules/$(shell  uname -r)/build/

obj-m +=mcs9865.o
obj-m +=mcs9865-isa.o

default:
	$(RM) *.mod.c *.o *.ko .*.cmd *.symvers
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
load:
	insmod mcs9865.ko
unload:
	rmmod mcs9865

install:
	cp mcs9865.ko mcs9865-isa.ko /lib/modules/$(shell uname -r)/kernel/drivers/serial/
	depmod -A
	chmod +x mcs9865
	cp mcs9865 /etc/init.d/
	ln -s /etc/init.d/mcs9865 /etc/rc.d/rc3.d/Smcs9865 || true  	
	ln -s /etc/init.d/mcs9865 /etc/rc.d/rc5.d/Smcs9865 || true
	modprobe -v mcs9865
	modprobe -v mcs9865-isa	

uninstall: etc etc



Any other ideas?
Thanks Ernie

---

### Post by bakegoodz on 2011-07-28
I think whitethorn is right. The "make install" script is probably loading a kernel module that isn't coming up on startup.
When it is working do this while in the same folder: lsmod > 1
Then reboot: lsmod > 2 Then: diff 1 2
See what module is different and put the module name in /etc/modules
You can manually load the kernel module with: modprobe themodulesname

---

### Post by Slim Odds on 2011-07-28
> **bakegoodz said:**
> I think whitethorn is right. The "make install" script is probably loading a kernel module that isn't coming up on startup.
When it is working do this while in the same folder: lsmod > 1
Then reboot: lsmod > 2 Then: diff 1 2
See what module is different and put the module name in /etc/modules
You can manually load the kernel module with: modprobe themodulesname

I think that it would be easier to just look at the make file and see what it's doing.

---

### Post by ESimard on 2011-07-28
Hi, More tests etc

The diff between working and not working are the two files 

mcs9865 and mcs9865-isa

I manually did a modprob

ernie@ernie-desktop:~/Desktop/MCS9865_Linux/MCS9865_V1.0.0.9$
sudo modprobe -v mcs9865
insmod /lib/modules/2.6.32-33
generic/kernel/drivers/serial/mcs9865.ko
 
ernie@ernie-desktop:~/Desktop/MCS9865_Linux/MCS9865_V1.0.0.9$ sudo modprobe -v mcs9865-isa
insmod /lib/modules/2.6.32-33-generic/kernel/drivers/serial/mcs9865-isa.ko

The drivers are now present and the ports defined.

I edited the /etc/modules 

 ernie@ernie-desktop:/etc$ cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
modprobe mcs9865
modprobe mcs9865-isa


After a reboot the modules still do not appear with lsmod.  I also tried adding the .ko to both modules entries with the same results.

Dang drivers just will not stay put.

Could there be some permission problem?
_Ernie

---

### Post by whitethorn on 2011-07-28
Well your almost there.  This should give you everything you need. You only have a small syntax failure.

[https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

---

### Post by ESimard on 2011-07-28
Guess I'm a total dunce, I don't see it.
_Ernie

---

### Post by whitethorn on 2011-07-29
Just list the module names without the modprobe command. 

```

lp
mcs9865
mcs9865-isa

```

---

### Post by ESimard on 2011-07-29
OK, I listed the names in /etc/modules, rebooted without any "make install", but the drivers are not installed.

ernie@ernie-desktop:/etc$ cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
modprobe mcs9865
modprobe mcs9865-isa

Do they need to be listed somewhere else?
Thanks Ernie

---

### Post by Slim Odds on 2011-07-29
> **ESimard said:**
> OK, I listed the names in /etc/modules, rebooted without any "make install", but the drivers are not installed.

ernie@ernie-desktop:/etc$ cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
modprobe mcs9865
modprobe mcs9865-isa

Do they need to be listed somewhere else?
Thanks Ernie

Remove the "modprobe", just list the modules. Like whitehorn said

---

### Post by ESimard on 2011-07-29
Haaa, senior moment, at 70 plus sometimes its difficult.

Thanks to all of you for your help.
All works correctly.
_Ernie

---

