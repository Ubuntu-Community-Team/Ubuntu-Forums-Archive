---
title: "Using DKMS to automagically build rr26xx after kernel update"
date: 2010-11-29
forum: General Help
---

### Post by rumblpak on 2010-11-29
Hi,

I am trying to setup dkms to automagically build the rr26xx driver for a rocketraid 2640x4 card when the kernel is updated.

I followed [this guide]("https://help.ubuntu.com/community/RocketRaid") which sounded like exactly what I was looking for.

When I get to the step where you actually use dkms to build the module with:
```
sudo dkms build -k `uname -r` -m rr26xx -v 1.2
```

I got the following error:
```
scripts/Makefile.build:49: *** CFLAGS was changed in "/var/lib/dkms/rr26xx/1.2/build/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
```

After a bit of poking around, I found that CFLAGS was actually being defined in /usr/src/rr26xx-1.2/inc/linux/Makefile.def, and after changing it to EXTRA_CFLAGS the error disappeared.

BUT... a challenger appeared in the form of a new error:

```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-23-generic -C /lib/modules/2.6.35-23-generic/build M=/var/lib/dkms/rr26xx/1.2/build....

Error!  Build of rr26xx.ko failed for: 2.6.35-23-generic (x86_64)
Consult the make.log in the build directory
```

Make.log contains the following:
```
make: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
```

What gives?

My current theory is that the make command is trying to build /lib/modules/2.6.35-23-generic/build instead of /var/lib/dkms/rr26xx/1.2/build, but I can't find where this command is defined in either the make file or its includes.

Any help or pointers in the right direction would be very appreciated, if my kernel gets updated by accident my raid array could go *poof* and that would be **very** bad.

I am running Ubuntu Server 10.10 x64 and am currently using the rr26xx driver as manually built using make && make install.
Using that process works, but I would like to have dkms take care of this for me instead of having to make && make install after every kernel upgrade.

Thanks!

---

### Post by foureight84 on 2010-12-31
Have you been able to find a solution to this? I'm seeing the same errors with my install.

---

### Post by lasersquid on 2011-01-01
I wasn't building the same module as this, but I got a similar error. Turns out my BUILT_MODULE_NAME and BUILT_MODULE_LOCATION were incorrect. I'd recommend actually navigating to the source directory running make, and checking the module name and location.

For reference, the output of my successful dkms build was:
```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.36-ARCH -C /lib/modules/2.6.36-ARCH/build M=/var/lib/dkms/rtl8192/0019/build....
```
So that part of your dkms output was not unusual.

Hope this helps you.

---

### Post by jkounis on 2011-01-07
I had precisely the same problem. Thank you to rumblpak for the information about fixing the Makefile.def file. For me, the following worked. (You have to start from the director where you extracted rr2640-linux-src-v1.2.)
```
cd inc/linux
cp Makefile.def Makefile.def.orig
sed -i -e 's/^CFLAGS/EXTRA_CFLAGS/' -e 's/(CFLAGS/(EXTRA_CFLAGS/' Makefile.def

```

Then, I had to edit the dkms.conf file. Here's the one that worked for me:
```
MAKE[0]="make"
BUILT_MODULE_NAME[0]=rr26xx
DEST_MODULE_LOCATION[0]=/kernel/drivers/scsi
PACKAGE_NAME=rr26xx
PACKAGE_VERSION=1.2
AUTOINSTALL=yes
POST_BUILD="do_Module.symvers rr26xx save $dkms_tree/$module/$module_version/build/Module.symvers"
REMAKE_INITRD=yes

```

I'm not positive if the "REMAKE_INITRD" directive is necessary, but it doesn't seem to hurt.

This resulted in the following build:
```
sudo dkms build -k `uname -r` -m rr26xx -v 1.2

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-24-generic....
cleaning build area....

DKMS: build Completed.

```

Now I need to wait for the next kernel update to see if it really worked. 

I hope this helps.

---

### Post by foureight84 on 2011-02-24
Did DKMS build work correctly? I haven't had a chance to give this a try since I last posted.

---

### Post by prcm311 on 2011-10-09
I'm a little late to the party but I wanted to confirm that jkounis' method works with the 1.3 driver on 2.6.32-34-server.  Thank you for taking the time to figure this out.

---

