---
title: "Kernel Compiling Error with 2.6.15-23 ubuntu Kernel"
date: 2006-06-10
forum: General Help
---

### Post by barakaspeed on 2006-06-10
From my previous [thread]("http://www.ubuntuforums.org/showthread.php?t=192207") I learned that I was getting high cpu usage running the 686 kernel on my Pentium M 1.6 chip.  So I apt-get linux-386 and it worked perfectly now.

Well I'm the type to keep tweaking and prying with things.  I really want to keep the 686 kernel for the added optimizations.  I read somewhere that it is probably the SMP in the 686 kernel that's conflicting with my Pentium M that doesn't need that at all anyway. 

Well I first followed these instructions to create a basic 686 kernel with no SMP support:

[http://www.ubuntuforums.org/showthread.php?t=157560&highlight=kernel+SMP](http://www.ubuntuforums.org/showthread.php?t=157560&highlight=kernel+SMP)

Well, it worked.  I had a 686 kernel with low cpu usage with no SMP support.  Perfect, but that new version also needed a lot more work to get wireless and other devices working again.  I wasn't really up for that challenge yet.  So I figured I could follow the same steps and rebuild the kernel that shipped with 6.06, 2.6.15-23.

Well ironically, compiling this source errored out and wouldn't compile a deb package so I could make it a kernel.  I didn't' save the error codes when I compiled it last, but did it save them somewhere in /var/log  so I can post them here?

I did follow this HOWTO and still errored out.
[https://wiki.ubuntu.com/KernelHowTos](https://wiki.ubuntu.com/KernelHowTos)


Anybody have some direction I can take with this?

---

### Post by Quirky on 2006-06-10
[https://wiki.ubuntu.com/KernelCompileHowto](https://wiki.ubuntu.com/KernelCompileHowto)

That page can't fail. Try compiling first without changing anything at all. Then remove SMP and see how it goes.

---

### Post by barakaspeed on 2006-06-10
No go.. :(

I followed it exactly except for one part.   Where it says ```
apt-get install linux-tree-2.6.8.1
``` I typed this instead ```
apt-get install linux-source-2.6.15
```

The reason for this is I couldn't' find any linux-tree-2.6.15 repositories.  Other than that, I followed it verbatim not modifying the kernel config at all.  

I'm attaching the tail end of the output from compiling from the console.  (If there is a complete log file somewhere I'll grab that too if you can tell me where it resides.)

And here is again what I typed line for line:
```

#apt-get install linux-source-2.6.15
#cd /usr/src
#tar jxvf linux-source-2.6.15.tar.bz2
#ln -s linux-source-2.6.15 linux
#cd /usr/src/linux
#cp /boot/config-2.6.15-23-686 .config
#make oldconfig
(I didn't do any make xconfig or anything just so I can see if I can just build a kernel)
#make-kpkg clean
#make-kpkg --stem linux --revision=custom.1.0 kernel_image

```

---

### Post by konradsa on 2006-06-10
This problem is all to familiar to me. Use make menuconfig (or make xconfig) and deactivate Device Drivers - USB Support - USB Networt Adapaters - USB ZD 1211(...)

Then your kernel will compile cleanly. This fix will of course only help you when you don't use a ZD1211 network adapter! :-) I wonder when will they finally fix that!

-- Sascha

---

### Post by barakaspeed on 2006-06-11
konradsa, thanks for the advice.  I was able to compile the kernel successfully.  Just my luck, after all the frustration of trying to compile it, when I try to boot into I get a kernel panic stating it can't find/mount VFS or something like that.   Whelp, I guess back to 386 for now.  I think I have a lot more reading to really understand what I'm doing with kernel compilations.

Thanks for the help!

---

### Post by konradsa on 2006-06-11
[QUOTE=barakaspeed]konradsa, thanks for the advice.  I was able to compile the kernel successfully.  Just my luck, after all the frustration of trying to compile it, when I try to boot into I get a kernel panic stating it can't find/mount VFS or something like that.   Whelp, I guess back to 386 for now.  I think I have a lot more reading to really understand what I'm doing with kernel compilations.

Thanks for the help![/QUOTE]


You need to use the initrd option when compiling the kernel, this is what I use and it works for me:
make-kpkg --initrd --append-to-version=[ENTER-STRING] kernel_image kernel_headers

and then install the two deb packages (headers and image). And make sure the right filesystems are compiled into your kernel.

---

