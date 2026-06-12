---
title: "Ubuntu + Debian OpenMosix packages"
date: 2005-02-25
forum: General Help
---

### Post by millerb on 2005-02-25
Has anyone tried the OpenMosix packages from Debian unstable (since they aren't in restricted, multiverse, or universe) and gotten an Ubuntu machine to work with other Debian proper OM machines?

Here's my process:

Other machines (this process works fine)
1. Install Debian sarge -> unstable
2. Get vanilla 2.4.26 from kernel.org
3. Patch said kernel with the latest OM kernel patch from the project web site
4. Compile and boot said kernel
5. apt-get install openmosix openmosixview
6. Machine is ready to be a node

Ubuntu machine
1. Install Warty -> Hoary (no problems)
2. Copy over unstable apt lines in sources.list from above machines
3. Do steps 2-5 from above.
4. Machine starts openmosix, other nodes can see it is OM compliant, but it isnt able to participate with the cluster.

I doubt many others have even tried this... :-P

---

### Post by mrmmo on 2005-03-05
Thanks for the info! great idea.
I'll try as soon as possible...  :D  :D

---

### Post by millerb on 2005-03-05
I got it working a while ago.  All I needed to to was recompile the kernel because I missed one or two options that seem to have been required.

---

### Post by thegreedyturtle on 2005-04-11
Mind detailing a bit more about what was needed?

I've been trying to get openMosix working for a while now...

---

### Post by millerb on 2005-04-11
I'd be happy to explain further, but I'd like for you to tell me exactly what you need help with.

---

### Post by thegreedyturtle on 2005-04-11
Skip this post and read the next one... I'm just going to leave this up as a bit of history.

I guess right now I'm hung up on the actual compilation and install of the kernel.

My process up to this point is:
1. Download 2.4.26-1 kernel source and extract it to /usr/src/ 
      Make a link with: ln -s linux-2.4.26/ linux for fun and profit
2. Download openmosix source from: [http://cogent.dl.sourceforge.net/sourceforge/openmosix/openMosix-2.4.26-1.bz2](http://cogent.dl.sourceforge.net/sourceforge/openmosix/openMosix-2.4.26-1.bz2)
      Extract to /usr/src/linux
3. Patch it with the command:
      patch -Np1 < openMosix-2.4.26.-1
4. Configurate it with:
      make xconfig
Note:
after an apt-get install modutils, i've actually got a .deb package created.

Now I just have to do the actual compilation...
And now I'm up to my ears in options... on [http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto), it says to use make-kpkg, but the actual command used gives me this error:
```

root@mars:/usr/src/linux # make-kpkg --append-to-version=.openmosix kernel_image --initrd binary
Warning: You are using the initrd option, that may not
work unless you have applied the initrd cramfs patch to
the kernel, or modified mkinitrd not to use cramfs by
default. The  cramfs initrd patch, is included in the
Debian supplied kernel sources, but is not present in
pristine kernel sources.
By default, I assume you know what you are doing, and I
apologize for being so annoying. Should I abort[Ny]?

```
Taking out the --initrd binary part starts a compile and it goes on it's merry way until it finally exits with this error:
```
make[3]: Leaving directory `/usr/src/linux-2.4.26/arch/i386/lib'
cd /usr/src/linux/debian/tmp-image/lib/modules/2.4.26-om1.openmosix; \
mkdir -p pcmcia; \
find kernel -path '*/pcmcia/*' -name '*.o' | xargs -i -r ln -sf ../{} pcmcia
if [ -r System.map ]; then /sbin/depmod -ae -F System.map -b /usr/src/linux/debian/tmp-image -r 2.4.26-om1.openmosix; fi
Version requires old depmod, but couldn't run /sbin/depmod.modutils: No such file or directory
make[2]: *** [_modinst_post] Error 2
make[2]: Leaving directory `/usr/src/linux-2.4.26'
make[1]: *** [real_stamp_image] Error 2
make[1]: Leaving directory `/usr/src/linux-2.4.26'
make: *** [kernel-image-deb] Error 2

```

I've found this: [http://episteme.arstechnica.com/eve/ubb.x/a/tpc/f/96509133/m/692005320731](http://episteme.arstechnica.com/eve/ubb.x/a/tpc/f/96509133/m/692005320731) as of 5:36 EST, and I'm gonna work on that for now.

Other than that, can you think of any 'gotchas' that are going to get in the way?

Oh, and what did you use for your grub menu? Did you just use the initrd that comes with Ubuntu?
Reference: (this is the original grub menu for Ubuntu)
```
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.10-5-386
savedefault
boot
```

Maybe something like this?
```

title		Ubuntu with openMosix 2.4.26
root		(hd0,0)
kernel		/vmlinuz-2.4.26.openmosix root=/dev/hda2 ro quiet splash
initrd		/initrd.img-2.6.10-5-386
savedefault
boot
```

---

### Post by millerb on 2005-04-11
Drop the initrd.  You simply don't need it.

In /usr/src/linux:

$ rm -f stamp*
$ make-kpkg --append_to_version openmosix kernel_image modules_image

The first command cleans up the previous make-kpkg attempt.

Then:

$ cd /usr/src/
$ dpkg -i kernel-image<tab><tab><enter>

dpkg should invoke update-grub automatically.

That's it, assuming your kernel config is correct.

---

### Post by thegreedyturtle on 2005-04-11
Whoops - Gnome just got crushed when I booted... locked the whole system up too, I'm gonna go back and try that.

---

### Post by millerb on 2005-04-11
[QUOTE=thegreedyturtle]Whoops - Gnome just got crushed when I booted... locked the whole system up too, I'm gonna go back and try that.[/QUOTE]


Some things won't work properly with Ubuntu, like udev, since it is not supported in 2.4.x.  These should get automatically disabled at boot and shouldn't affect Gnome.  But, who knows if something else critical depends on 2.6.x.

---

### Post by thegreedyturtle on 2005-04-11
Yeah I caught that when I booted last. (I didn't get too much further than that though... )

I've been keeping my eye on: [http://openmosix.snarc.org/](http://openmosix.snarc.org/) for 2.6 stuffs.

---

### Post by millerb on 2005-04-11
> Migration is fully working (manual migration only at the moment)

IMO, that makes the 2.6 unofficial worthless.

---

### Post by thegreedyturtle on 2005-04-11
Pretty much, the main selling point of openMosix is it's automatic thread migrating. 

But they never claim that it's really ready to go at all either - but it's nice to know that at least someone is working on updating it to 2.6


Update:

After a lengthy compile time, I installed the new .deb package, and now I'm getting a kernel panic VFS, unable to mount root fs.

```

VFS: Cannot open root device "hda2" or 03:02
Please append a correct "root=" boot option
Kernel panic: VFS: Unable to mount root fs on 03:02

```

This is just a guess, but I'm figuring that I didn't include the correct drivers in the kernel when I compiled it...

---

### Post by millerb on 2005-04-11
Did you forget to compile in the right FS drivers?  You don't need to append a root= line to grub....I used ext3 when I did Ubuntu + OpenMosix.

---

### Post by thegreedyturtle on 2005-04-11
[QUOTE=millerb]Did you forget to compile in the right FS drivers?  You don't need to append a root= line to grub....I used ext3 when I did Ubuntu + OpenMosix.[/QUOTE]
 I use ext3 as well, and it was selected as 'm' in the kernel options list. I switched it over to yes, and I'm recompiling... probably take another hour.

What does m stand for - modular? (I guess it can't really get to the modules if it can't open the root fs!)

---

### Post by millerb on 2005-04-11
m == module...YOU MUST have the file system of your / partition set to * (built in).

---

### Post by thegreedyturtle on 2005-04-13
[QUOTE=millerb]m == module...YOU MUST have the file system of your / partition set to * (built in).[/QUOTE]
By including the mouse in the kernel, I can actually get the x server to start up, but it can't start gnome-panel, nautilus ect ect, you know those things that are handy for gnome to do it's thang.

Sadly, it appears that this is all due to Ubuntu's incompatability with the 2.4.x kernel, and there are no plans on looking back.

Other than that it appears to be working fine. Albeit, I have done very little testing.

---

### Post by rick_1010 on 2006-10-02
> **millerb said:**
> Has anyone tried the OpenMosix packages from Debian unstable (since they aren't in restricted, multiverse, or universe) and gotten an Ubuntu machine to work with other Debian proper OM machines?

Here's my process:

Other machines (this process works fine)
1. Install Debian sarge -> unstable
2. Get vanilla 2.4.26 from kernel.org
3. Patch said kernel with the latest OM kernel patch from the project web site
4. Compile and boot said kernel
5. apt-get install openmosix openmosixview
6. Machine is ready to be a node


I'm doing this right now, I gave up on trying to make OpenMosix work with Ubuntu directly as it seems easier to downgrade the kernel in Debian. Glad to hear that it worked for you as I have been trying for too long to get an OpenMosix cluster up and running (prior to this I had only gotten it to work on Fedora Core 1 which is basically useless).

---

### Post by millerb on 2006-10-02
I haven't used OpenMosix since I last posted, so I can't offer an updated method for Ubuntu 6.06+.

I hope someone else picks up where I left off.

---

### Post by rick_1010 on 2006-10-03
Hi,
  I am following this guide: [http://clusterlab.bzzz.net/doku.php?id=openmosixondebiansarge](http://clusterlab.bzzz.net/doku.php?id=openmosixondebiansarge) to downgrade the kernel in Debian and install OpenMosix on it, however it doesn't seem to be working, if you could help I would greatly appreciate it (just if you have a suggestion of what I could do differently from the guide)

Thanks

---

### Post by funkyade on 2006-10-27
Just wondering if anyone has successfully got a 2.6 kernel compiled and running under Edgy?

Haven't tried yet but curious if anyone else has tried?

Currently getting the stuff from openmosix.snarc.org.

---

