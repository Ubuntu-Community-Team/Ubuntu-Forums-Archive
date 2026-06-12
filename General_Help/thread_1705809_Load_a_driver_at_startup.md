---
title: "Load a driver at startup"
date: 2011-03-12
forum: General Help
---

### Post by threedogs on 2011-03-12
I got a 6-port Syba serial card. The make went OK and I can manually load the drivers by opening a terminal, changing to the driver directory and...

sudo insmod mcs9865.ko
sudo insmod mcs9865-isa.ko

That loads the drivers and the new serial ports work great, but I want the modules to load automatically at boot. I copied the drivers to...

/lib/modules/2.6.27-17-generic/kernel/drivers/serial

Then I added two lines to etc/modules...

mcs9865.ko
mcs9865-isa.ko

The drivers are not loading. Anyone know what I'm doing wrong?

John

---

### Post by Krytarik on 2011-03-13
Try it without ".ko".

Greetings.

---

### Post by lithopsian on 2011-03-13
onsmod?  New century, new command.  Use modprobe for your experimentation and testing, because that's the command that will be used to load the module at boot.  It works from anywhere and you don't specify the ko.  It also doesn't care whether you have a dash or an underscore in the name, takes care of module dependencies, and is overall so easy to use that you should forget insmod even exists :)

Also make sure your modules aren't blacklisted.  I don't think these are but check on your setup.

---

### Post by threedogs on 2011-03-13
Krytarik,

I've tried both with the .ko and without in etc/module with no luck.

lithopsian,

Methinks thou dost speak too harshly of insmod. Seriously, though, I was just following the driver readme. I'll use modprobe now. But that has nothing to do with my auto load problem, right? I'm having a hard time finding good information on how this is supposed to work. There is a lot of info on the web, but there seems to be several ways to make this happen (compile the kernel, messing about with init.d,using modules.conf (obsolete), etc...
I know my modules work. I don't think they are blacklisted but don't know how to check. I'd love some kind of checklist.
1. make the driver and confirm it works (done)
2. append the driver names to etc/modules (done)
3. copy the drivers where they can be found ie. lib/modules/kernel... (done)
4. is there another step to make executable or add permissions or something?

John

---

### Post by threedogs on 2011-03-13
Got it to work. Interesting thing was that insmod worked, modprobe did not. A little Googling and I discover depmod was required. So the procedure is...
1. download the driver and extract
2. open terminal and change to the newly created directory
3. "make" (no sudo required)
4. copy the mcs9865.ko and mcs9865-isa.ko to /lib/modules/2.6.27-17-generic/kernel/drivers/serial
5. edit /etc/modules and add a line "mcs9865"
6. "depmod -a"
7. reboot

---

### Post by lithopsian on 2011-03-13
depmod is needed if you install modules manually.  Installation by deb, aptitude, or by a kernel build, should create the module dependencies automatically.  There is probably a "make install" for your drivers and it *should* do the depmod for you as well as copying the drivers into the correct location.  Or maybe it does all this, but only if you sudo since it would require root privileges.  Same for depmod, it would normally need root access.

I only say use modprobe because that is what will be used when you boot.  No point testing with one program and then complaining if a different program doesn't work ;)  modprobe calls insmod, rmmod, and anything else it needs to get the job done, but it is smart about it and examines a number of configuration files to work out what it should be doing.

---

### Post by threedogs on 2011-03-14
Thank you for your help - your advice was spot on and led directly to a solution. The makefile did not work. I don't think it was written with Debian systems in minds. All it seems to do is place a file called mcs9865 in the init.d folder. All other files in init.d are scripts, but mcs9865 is simply a 2-line text file saying

```
modprobe mcs9865.ko 
modprobe mcs9865-isa.ko
```

Here is the entire makefile if you are interested. If you can figure out an easy way to make this work, I'll try it on my system and let Moschip know so they can fix.
```


KDIR:=/lib/modules/$(shell  uname -r)/build/

DEBIAN_VERSION_FILE:=/etc/debian_version
DEBIAN_DISTRO:=$(wildcard $(DEBIAN_VERSION_FILE))

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
ifeq ($(DEBIAN_DISTRO), $(DEBIAN_VERSION_FILE))
	ln -s /etc/init.d/mcs9865 /etc/rcS.d/Smcs9865 || true
else
	ln -s /etc/init.d/mcs9865 /etc/rc3.d/Smcs9865 || true  	
	ln -s /etc/init.d/mcs9865 /etc/rc5.d/Smcs9865 || true
endif
	modprobe mcs9865
	modprobe mcs9865-isa	

uninstall:
	modprobe -r mcs9865
	modprobe -r mcs9865-isa
	rm /lib/modules/$(shell uname -r)/kernel/drivers/serial/mcs9865*
	depmod -A
	rm -f /etc/init.d/mcs9865
ifeq ($(DEBIAN_DISTRO), $(DEBIAN_VERSION_FILE))
	rm -f /etc/rcS.d/Smcs9865
else
	rm -f /etc/rc3.d/Smcs9865
	rm -f /etc/rc5.d/Smcs9865
endif

clean:
	$(RM) *.mod.c *.o *.ko .*.cmd *.symvers *.order *.markers
	$(RM) -r .tmp_versions
```

---

