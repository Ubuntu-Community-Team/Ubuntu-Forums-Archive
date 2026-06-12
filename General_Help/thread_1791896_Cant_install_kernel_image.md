---
title: "Cant install kernel image"
date: 2011-06-27
forum: General Help
---

### Post by Eric1987 on 2011-06-27
I need module init tools 3.13 or higher. I have tried to install them from .debs I've found but after doing the make install it doesn't install them! then it says to do depmod but nothing works still! Also my wifi is super slow I have a realtek 8192CU. If I tether my phone my internet speeds are normal.

---

### Post by insanity54 on 2011-06-27
Could you post some more info, like a broader description of what you're trying to accomplish?

If you're trying to install a .deb, you don't do:```
make install
```

you would do:```
sudo dpkg -i package.deb
```

---

### Post by Eric1987 on 2011-06-27
2). ./configure
	    (optionally specify "--prefix" or "--mandir" for non /usr/local)
	3). make
	4). make install
	5). depmod
	    (to update /lib/modules/<kernel version> for the latest release)

Thats what I do and it doesn't install.

---

### Post by Eric1987 on 2011-06-27
Bump still cant get it figured out!

---

### Post by garvinrick4 on 2011-06-27
From Read Me file in module-init-tools in 3.13   
The install file says ./configure the make then make install ect. ect. ect.
but refers to Read Me file and other packages must be installed also I believe.
Requirements:
    - A 2.6 series Linux kernel with sysfs, procfs, and loadable module
      support enabled in the kernel configuration. It is also required
      that sysfs and procfs be mounted in their usual /proc and /sys
      locations in order for certain functionality to be provided.

    - Module remove support must be enabled if removing is required. Yo
      can also enable other options such as forced removal, but this is
      really a bad idea for anything other than development.

    - Module versioning (MODVERSIONS) must be enabled if you would
      like to try to use modules from one kernel with another, similar
      one without the kernel complaining loudly at the difference.

---

### Post by insanity54 on 2011-06-27
> **Eric1987 said:**
> 2). ./configure
	    (optionally specify "--prefix" or "--mandir" for non /usr/local)
	3). make
	4). make install
	5). depmod
	    (to update /lib/modules/<kernel version> for the latest release)

Thats what I do and it doesn't install.

I think #4 needs to be with elevated privileges:```
sudo make install
```

If it were me though I would use "checkinstall", instead of "make install":```
sudo checkinstall
```

If you use checkinstall it would go like this:```
./configure
make
sudo checkinstall
depmod? (I've never used depmod)
```

checkinstall will let you later manage the installation with synaptic. (uninstall)

Are there errors displayed when you entered the "make" code? Can you post them?

---

### Post by garvinrick4 on 2011-06-27
I believe the OP is trying to install 3.0 rc4 oneiric in 11.04.
I am running rc2 with no problems, rc4 not yet.
If any user has installed the rc4 version of 3.0 kernel in 11.04 chime in please.

Here is rc2 which works with natty out of box need 3 of them, all.deb, headers and image of your 32 or 64 bit install:
[Index of /~kernel-ppa/mainline/v3.0-rc2-oneiric]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-rc2-oneiric/")

---

