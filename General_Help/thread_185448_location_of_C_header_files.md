---
title: "location of C header files"
date: 2006-05-31
forum: General Help
---

### Post by closeyourwindows on 2006-05-31
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
```

where is this normally located because the default did not work and I am not sure where to look for this.

---

### Post by chriscando on 2006-05-31
I had to install it manually through synaptic, just did a quick search for it. After I did that the location was set by default, it was something like /usr/src/linux-headers-2.6.12-10/

---

### Post by closeyourwindows on 2006-05-31
```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.
```

here is more of the error, I am installing a program...

---

### Post by curtis on 2006-05-31
Your want to install the kernel headers package, linux-headers-2.6.12-10 I believe, not sure because I use Dapper.
Or just apt-get install linux-headers may help, linux-headers-686 for a 686 kernel.

---

### Post by closeyourwindows on 2006-05-31
```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]
```

I hit yes previously and installed the linux headers, but I am wondering if I need to change this setting

---

