---
title: "Trouble rebuilding kernel module"
date: 2011-01-06
forum: General Help
---

### Post by dental on 2011-01-06
Hi.

I need to rebuild a kernel module and I'd like the module to be compatible with the ubuntu distributed kernel.

I tried something along these lines:

* get the sources via: apt-get source linux-image-2.6.35-24-generic
* cd to the unpacked (and patched, I believe) directory: cd linux-2.6.35
* take kernel config that I'm currently running (I'm running 2.6.35-24-generic): cp /boot/config-2.6.35-24-generic .config
* build the module I care about: make drivers/usb/class/usblp.ko

The module is built, but when I try to load it, insmod fails and I see this in dmesg:

** usblp: no symbol version for module_layout**

I tried to generate the kernel config via debian/rules genconfigs, which resulted in the same config file (with the exception of the local version string). I tried building some other modules and loading them, but I always get that error on loading.

Thanks for any tips.

PS. I tried building all the modules via make modules, but I still got the same error. I need to rebuild the module to further investigate a funny issue I'm having and I'd like to stick with the official kernel to avoid trouble with out-of-tree modules, like vbox or nvidia.

---

### Post by Frogs Hair on 2011-01-06
I don't know if this will be of use , but I came across this last week.

[http://www.webupd8.org/2010/12/how-to-compile-kernel-in-ubuntu-easy.html](http://www.webupd8.org/2010/12/how-to-compile-kernel-in-ubuntu-easy.html)

[http://www.webupd8.org/2010/04/kernelcheck-fixed-deb-download-ubuntu.html](http://www.webupd8.org/2010/04/kernelcheck-fixed-deb-download-ubuntu.html)

---

### Post by dental on 2011-01-15
Frogs Hair: Thanks for the pointers. Unfortunately they were too generic.

I've devised some sort of hacky solution, so I'll add it in another post in case anyone ever faces the same issue.

---

### Post by dental on 2011-01-15
So, it turns out that there's some more magic going on in the build of the kernel.

If you just get the sources and then use the kernel Makefile in a straightforward way, you get a module that's incompatible with the distro kernel. The Debian/Ubuntu kernel build process does some things that the straightforward way skips.

Part of the problem probably has to do with Module.symvers (you need to have the file and it must be the same as what was used to build the distro kernel) - though I wasn't too lucky in googling more info about this... And this is probably not the only magic thing that there is.

So I thought I'd just build the whole kernel the Debian/Ubuntu way:

```

cd linux-2.6.35
debian/rules build

```unfortunately this is a really lengthy and disk-space-consuming process. I ran out of HDD space on my laptop. So I did an *ugly* thing - I hacked the build script. It turns out the debian/rules script (a Makefile in fact) includes makefile fragments from debian/rules.d. And the file 2-binary-arch.mk launches the actual kernel build. Specifically this part:

```

$(stampdir)/stamp-build-%: prepare-%
        @echo "Building $*..."
        $(build_cd) $(kmake) $(build_O) $(conc_level) $(build_image)
        $(build_cd) $(kmake) $(build_O) $(conc_level) modules
        @touch $@

```so what I did - I hacked the line ending with modules to build my module instead (plus added an exit to stop the process from continuing past that point) so it read:

```

        $(build_cd) $(kmake) $(build_O) $(conc_level) drivers/usb/class/usblp.ko
        exit 1
  
```This it quite ugly but at least it means your module is build in exactly the same environment (with the same options, in the same directory etc.) as it should be. - So after this patch just fire up debian/rules build and wait.

With this I got a module that could be successfully loaded into the kernel.

Maybe you could comment out the line building the kernel itself to make the process yet shorter, but I did not test this.

If anybody knows the proper way of doing this I'm all ears, of course. :)

---

### Post by dental on 2011-01-15
In fact in my case I had one more hoop to jump through: I'm running a 64bit kernel (x86_64), but I wanted the module built for 32bit (x86).

Building kernel in such situation (provided you have gcc multilib installed) is a simple matter of something like:

```

ARCH=i386 make ...

```

Cross-compiling with the Debian/Ubuntu rules script seems to be achieved by:

```

dpkg-architecture -ai386 -c debian/rules build

```

but in this case the kernel Makefile is instructed to look for compiler/linker/binutils/etc with the prefix i686-linux-gnu-, as if this was a real cross-compilation.

I don't know if there's a way to make the build script acknowledge the multilib toolchain and not ask for a cross-compile toolchain. But I just created a fake cross-toolchain (see [http://tinkering-is-fun.blogspot.com/2009/12/compiling-linux-kernel-for-x86-on-x8664.html](http://tinkering-is-fun.blogspot.com/2009/12/compiling-linux-kernel-for-x86-on-x8664.html)). Just use the correct prefix:

```

$ (echo &#8216;#! /bin/sh&#8217;; echo &#8216;exec gcc -m32 &#8220;$@&#8221;&#8216;) > i686-linux-gnu-gcc
$ chmod +x i686-linux-gnu-gcc
$ for i in ar ld nm objcopy strip; do
$   ln -s `which $i` i686-linux-gnu-$i
$ done

```(possibly not all are needed)

Then just add the directory where this fake toolchain was generated to PATH and fire up the cross compilation once again:

```

PATH=fake-cross-toolchain-path:$PATH dpkg-architecture -ai386 -c debian/rules build

```

Voilà! How simple. :)

PS. Maybe the requirement for the fake cross toolchain is in fact not caused by debian/rules but the way kernel treats this case has changed. (?)

---

