---
title: "Removed /usr/src, now need kernel sources"
date: 2010-03-16
forum: General Help
---

### Post by skkeeper on 2010-03-16
By some weird reason, I must have been drunk or something, I removed all the contents from /usr/src this weekend.

After that I was unable to compile a new kernel or even to install the NVIDIA drivers, I didn't mind to solve that since Lucid will be released soon and I thought: "ahh **** that, I'll leave the system without upgrading the kernel or the graphics driver till then".

Well this morning a new Xserver update was released and my graphics drivers stopped working immediately.

Now I can't reinstall them without the kernel sources. I already reinstalled the linux-image and the linux-source package but that didn't solve anything.

Any help would be extraordinary
Thanks

---

### Post by mikewhatever on 2010-03-16
It looks like what you deleted was linux-headers.
```
/usr/src$ ls
linux-headers-2.6.31-20  linux-headers-2.6.31-20-generic  nvidia-185.18.36
```

Try **sudo apt-get install linux-headers-generic**

---

### Post by skkeeper on 2010-03-16
I forgot to mention that package, I already installed that one: **no change**.

Maybe there is a problem detecting the sources because I changed the /usr/src/linux symlink before reinstalling the packages. Is that a problem?

---

### Post by lykwydchykyn on 2010-03-16
If you just delete the files, the package manager assumes that the headers package is still installed; so if you try to install it again, it won't do anything.

What you need to do is force reinstall:
```

sudo apt-get --reinstall linux-headers-generic

```

---

### Post by skkeeper on 2010-03-16
Already done that too.

Here is a ls from my /usr/src

```
skkeeper@grinkosmo-nix:~$ ls /usr/src/
linux         linux-2.6.33.tar.bz2             linux-source-2.6.31.tar.bz2
linux-2.6.33  linux-headers-2.6.31-20-generic  nvidia-185.18.36
```

---

### Post by slakkie on 2010-03-16
> **skkeeper said:**
> I forgot to mention that package, I already installed that one: **no change**.

Maybe there is a problem detecting the sources because I changed the /usr/src/linux symlink before reinstalling the packages. Is that a problem?


Did you remove the package first? Or did you issue a reinstall? Otherwise it is logical. You already have the package installed, so it will not reinstall it for you.

And I don't have an /usr/src/linux, and cannot find it with apt-file search and dpkg -S commands.

---

### Post by lykwydchykyn on 2010-03-16
> **skkeeper said:**
> Already done that too.

Here is a ls from my /usr/src

```
skkeeper@grinkosmo-nix:~$ ls /usr/src/
linux         linux-2.6.33.tar.bz2             linux-source-2.6.31.tar.bz2
linux-2.6.33  linux-headers-2.6.31-20-generic  nvidia-185.18.36
```

So it appears you have the headers.

Can you post the actual error you're getting, that may give clues as to what's actually missing.

---

### Post by skkeeper on 2010-03-16
I'm sorry I should have posted this earlier.

I get this on my NVIDIA installer:

```
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: The kernel header file
       '/lib/modules/2.6.31-20-generic/build/include/linux/kernel.h' does not
       exist.  The most likely reason for this is that the kernel source path
       '/lib/modules/2.6.31-20-generic/build' is incorrect.  Please make sure
       you have installed the kernel source files for your kernel and that they
       are properly configured; on Red Hat Linux systems, for example, be sure
       you have the 'kernel-source' or 'kernel-devel' RPM installed.  If you
       know the correct kernel source files are installed, you may specify the
       kernel source path with the '--kernel-source-path' command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

I have already tried your recommendations to purge and the install the headers. Still nothing. Thanks for your replys nonetheless

---

### Post by mikewhatever on 2010-03-16
You could try <sudo dpkg-reconfigure nvidia-185-kernel-source>.

---

### Post by lykwydchykyn on 2010-03-16
/lib/modules/2.6.31-20-generic/build should be a symlink to /usr/src/linux-headers-2.6.31-20-generic.

Is this the case?

---

### Post by skkeeper on 2010-03-16
> **mikewhatever said:**
> You could try <sudo dpkg-reconfigure nvidia-185-kernel-source>.

```
Error! Bad return status for module build on kernel: 2.6.31-20-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/185.18.36/build/ for more information.
```

tail of make.log
```
*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1
```


> /lib/modules/2.6.31-20-generic/build should be a symlink to /usr/src/linux-headers-2.6.31-20-generic.

Is this the case?

Yes.

```
skkeeper@grinkosmo-nix:/lib/modules/2.6.31-20-generic$ ls -al
total 3408
drwxr-xr-x  4 root root   4096 2010-03-16 19:36 .
drwxr-xr-x  6 root root   4096 2010-03-04 18:12 ..
lrwxrwxrwx  1 root root     40 2010-03-16 19:29 build -> /usr/src/linux-headers-2.6.31-20-generic

```

---

### Post by lykwydchykyn on 2010-03-16
So, if you navigate to /lib/modules/2.6.31-20-generic/build/include/linux/, does kernel.h exist?

---

### Post by skkeeper on 2010-03-16
Nop the file is not present.  :confused:

---

### Post by lykwydchykyn on 2010-03-16
Why do you have source for 2.6.33 in /usr/src?  Are you running an updated kernel from a ppa or something?

What does "uname -r" say?

Is there anything in that kernel headers folder?

---

### Post by skkeeper on 2010-03-16
I've used "Master Kernel's thread" here on Ubuntu forums to compile my own kernel, thats why I have some sources there.

But right now im running 2.6.31-20-generic, avaiable and installed from the standard repos.

---

