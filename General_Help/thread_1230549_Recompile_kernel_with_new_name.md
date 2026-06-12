---
title: "Recompile kernel with new name"
date: 2009-08-03
forum: General Help
---

### Post by lotus49 on 2009-08-03
I have been recompiling the Jaunty kernel for my Acer Aspire One (frustratingly just to change a single option) according to the instructions here -> [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile).  This worked fine while the version I was using was ahead of the standard version in that the fact that they were both called something-generic didn't matter.

Now the standard kernel has caught up with me and I need to know how to change the name of the resulting kernel to avoid a clash.  The above instructions say (quite rightly) "However, you also want to make sure that you do not clash with the stock kernels." but give no clue as to how.

I used to know how to do this a (long) while ago using --append-to-version but using the above instructions, it isn't clear if this is still possible.  I know I could create a new branch, but that is a fair bit of hassle for what is only a single option change.

So, how to I compile a (nearly) standard kernel with a new name?

I apologise if my searching has failed to find something obvious - believe me I have looked.

---

### Post by Locutus_of_Borg on 2009-08-03
This *should* work:
```

sudo -i
cd /usr/src/linux
sed -e -i 's|CONFIG_LOCALVERSION=""|CONFIG_LOCALVERSION="arbitrary_name"|ig' .config
make
cp arch/[your architecture]/boot/bzImage /boot/kernel
nano /boot/grub/menu.lst
```
Edit grub to boot the new kernel

---

### Post by ibuclaw on 2009-08-03
Have a look at the [Master Kernel thread]("http://ubuntuforums.org/showthread.php?t=311158") for reference:

But, to show you quickly, run the following to install all needed packages:
```
sudo apt-get install build-essential bin86 kernel-package wget fakeroot libncurses5 libncurses5-dev
```

To prepare the .config file (if one doesn't exist yet in the kernel source):
```
cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
```

To alter the .config file (and the modules/settings that are used in your kernel).
```
make menuconfig
```

And to build your kernel:
```
INSTALL_MOD_STRIP=1 fakeroot make-kpkg --initrd --append-to-version="-**AA1**" kernel_image kernel_headers modules_image
```
Change "AA1" with the name you want to have instead

Once that has finished, two .deb files will be created in the directory above, run the following to install:
```
sudo dpkg -i ../*.deb
```

Regards
Iain

---

### Post by Locutus_of_Borg on 2009-08-03
tinivole:

why the huge convoluted process?

OP already states he has compiled a kernel, so we can assume he has build tools, you are asking him to install wget (is that seriously not included with ubuntu?) yet make no use of it, you complicate the process by making deb files that by all intents and purposes should contain within them one file (the kernel) -- initrd need not be changed if localversion string is the only change (initrd need not even exist if he is compiling his own kernel), and suggest that he runs 'make menuconfig' and yet give no such advice as to what string needs to be changed in order to append a different version number.



it's been a while since i compiled a kernel under ubuntu, but i do not ever recall it being such a hassle, is there some reason why standard kernel compilation procedures do not work properly under ubuntu?

---

### Post by ibuclaw on 2009-08-03
> **Locutus_of_Borg said:**
> tinivole:

why the huge convoluted process?

OP already states he has compiled a kernel, so we can assume he has build tools, you are asking him to install wget (is that seriously not included with ubuntu?) yet make no use of it,
Copied from [Master Kernel thread]("http://ubuntuforums.org/showthread.php?t=311158"), don't shoot the messenger.

> **Locutus_of_Borg said:**
> you complicate the process by making deb files that by all intents and purposes should contain within them one file (the kernel)
The kernel is alot more than one file ... it's about 2000 files or modules.
make-kpkg will create 2 debian packages, one for the kernel, another for the kernel headers.
The great thing about packages is that it is easy to install, remove and upgrade a kernel without worrying about conflicts (dpkg will resolve them within debian/ubuntu's package management system).
> **Locutus_of_Borg said:**
>  -- initrd need not be changed if localversion string is the only change (initrd need not even exist if he is compiling his own kernel), and suggest that he runs 'make menuconfig' and yet give no such advice as to what string needs to be changed in order to append a different version number.
Again, packages will (or should) sort this out. In terms of version numbers for the same kernel directory, dpkg will uninstall the previous kernel/install new kernel in same directory.


> **Locutus_of_Borg said:**
> 
it's been a while since i compiled a kernel under ubuntu, but i do not ever recall it being such a hassle, is there some reason why standard kernel compilation procedures do not work properly under ubuntu?
I don't see it as a hassle. I'm just being thorough.

All you need be concerned about is this line:
INSTALL_MOD_STRIP=1 fakeroot make-kpkg --initrd --append-to-version="-AA1" kernel_image kernel_headers modules_image

**INSTALL_MOD_STRIP=1** dramatically reduces the size of the kernel.
**--initrd** is included as I've had times where I've booted into an unbootable kernel because the option wasn't used in compilation/package stage.
**--append-to-version** is what the OP asked for confirmation about.
**modules_image** is the only thing that is not needed (deprecated feature, used to do something way back in slackware days, habits died hard).

---

### Post by lotus49 on 2009-08-03
Thanks to both of you for your answers.

To answer the question about tinivole's method, this is actually very similar to what I am already doing and I do want to create deb files as using the package management system should avoid any possibility of leaving my system unbootable.

Also all I have to do is just run the:

```
INSTALL_MOD_STRIP=1 fakeroot make-kpkg --initrd --append-to-version="-AA1" kernel_image kernel_headers modules_image
```
line as I have effectively done all the rest.  BTW I had to replace -AA1 with something lower case (I chose -aspireone for all the difference it makes.

I hadn't compiled a kernel for years until I bought my Aspire One and I wish I hadn't had to then either.  The process has changed a lot since the days when I used to do it and it is now far from obvious.  I know that users are discouraged from compiling their own kernels, but unfortunately, sometimes it's necessary to support the hardware.

---

### Post by Locutus_of_Borg on 2009-08-03
to be fair, the kernel is simply the bzImage file, the kernel modules would have been installed with 'make modules_install' that i would have mentioned had the OP been upgrading kernels and not simply changing the localversion string, the modules he is currently using will continue to work as the main kernel version is not changing (i.e. 2.6.30 vs 2.6.30-*version*)

the biggest hassle in compiling a kernel is sorting through the hundreds of parameters via menuconfig (or xconfig, etc.), after which I like to let 'make' and 'cp' do all the real work.  I understand the advantages of using packages though as I currently have five sub-directories under /lib/modules/ and this is a rather recent install, but are you saying dpkg will actually remove a previous kernel version's modules?

also, i believe --append-to-version is equivalent to CONFIG_LOCALVERSION
and the only time i have needed an initrd was when i was forced to pre-load usb modules in order to boot off of an external hard drive, otherwise as long as you build the kernel with all necessary requirements for your hardware, you do not need an initrd

i am curious though if you know how CONFIG_CC_OPTIMIZE_FOR_SIZE and INSTALL_MOD_STRIP relate?  I always use the former, is there a difference between them? (the first merely passes '-Os' to the compiler) can they be used in conjunction?

---

### Post by ibuclaw on 2009-08-03
> **Locutus_of_Borg said:**
> i am curious though if you know how CONFIG_CC_OPTIMIZE_FOR_SIZE and INSTALL_MOD_STRIP relate?  I always use the former, is there a difference between them? (the first merely passes '-Os' to the compiler) can they be used in conjunction?

Good question ...

As you've already said, CC_OPTIMIZE_FOR_SIZE is just passing -Os to cc.
As far as I'm aware, INSTALL_MOD_STRIP is similar to 'strip --strip-unneeded' (I may be misinformed though).
Which may get just that little bit more off of the size of the library.

ie: A simple 'Hello' app.
```

iain@jstdio:~$ gcc -Os hello.c
iain@jstdio:~$ du a.out 
**12	a.out**
iain@jstdio:~$ ./a.out
**Hello World**
iain@jstdio:~$ strip --strip-unneeded a.out 
iain@jstdio:~$ du a.out 
**8	a.out**
iain@jstdio:~$ ./a.out
**Hello World**
iain@jstdio:~$ 

```

---

