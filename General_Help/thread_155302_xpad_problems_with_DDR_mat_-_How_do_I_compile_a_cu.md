---
title: "xpad problems with DDR mat - How do I compile a custom kernel module?"
date: 2006-04-04
forum: General Help
---

### Post by grendel_khan on 2006-04-04
I recently acquired a DDR mat and a physical adapter so I could use StepMania.

Tailing syslog when I plugged it in, I saw: ```
Apr  4 19:38:02 localhost kernel: [4295426.039000] input: X-Box pad on usb-0000:00:1d.1-2.1<6>usbcore: registered new driver xpad
Apr  4 19:38:02 localhost kernel: [4295426.039000] drivers/usb/input/xpad.c: X-Box pad driver:v0.0.5
Apr  4 19:38:02 localhost usb.agent[7482]:      xpad: loaded successfully
Apr  4 19:38:02 localhost input.agent[7564]:      evdev: already loaded
Apr  4 19:38:02 localhost input.agent[7552]:      evdev: already loaded
Apr  4 19:38:03 localhost input.agent[7524]:      joydev: already loaded
Apr  4 19:38:03 localhost input.agent[7524]:      evdev: already loaded
```
lsusb showed: ```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0c12:8809 Zeroplus Red Octane Ignition Xbox DDR Pad
Bus 002 Device 002: ID 0c12:8801 Zeroplus
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```
When I run StepMania, and go to the setup options, the buttons appear as axes. I can't press both left and right at the same time, which is necessary for DDR playing. I can confirm this by using **jstest --event /dev/js0**.

There is a modified version of xpad.c which uses a different mapping. There is available a [kernel patch](http://einsteinsbreakfast.com/demos/xpad-ddr-patch.diff) or just [a modified copy of xpad.c](http://einsteinsbreakfast.com/demos/xpad.c). I need to compile this as a module and use it. My questions:

[LIST]
[*]Do I need to apply a diff to a kernel source tree, or can just compile xpad.c?
[*]How do I compile xpad.c into a usable kernel module?
[*]Can I replace the current xpad.ko without messing up my kernel installation (like installing software in /usr/local instead of /usr to avoid conflicting with anything prepackaged), or should I just leave the changed module in my home directory?
[/LIST]

Thanks to anyone who can help me out with this...

---

### Post by John.Michael.Kane on 2006-04-04
[http://ubuntuforums.org/showthread.php?t=84174&highlight=kernel](http://ubuntuforums.org/showthread.php?t=84174&highlight=kernel)
[http://ubuntuforums.org/showthread.php?t=85064&highlight=kernel](http://ubuntuforums.org/showthread.php?t=85064&highlight=kernel)

---

### Post by grendel_khan on 2006-04-04
So I have to compile the entire kernel? I thought I could build a module with just the headers, and I didn't find any way to do that; it seemed a bit excessive to actually rebuild the entire kernel for one module.

---

### Post by John.Michael.Kane on 2006-04-04
[QUOTE=grendel_khan]So I have to compile the entire kernel? I thought I could build a module with just the headers, and I didn't find any way to do that; it seemed a bit excessive to actually rebuild the entire kernel for one module.[/QUOTE]


Well then dont compile the whole kernel.if you already know you need a kernel patch then make it. to me it came off as if you wanted the quickest method. since you seem to know what you doing then make the patch, and post it for those who may need it after you test that it is workig.

---

### Post by grendel_khan on 2006-04-04
I didn't make the patch; I just have a fixed version of one of the kernel source files, drivers/usb/input/xpad.c. I want to compile that into a kernel module, rmmod the stock one and insmod the fixed xpad.ko that I would have just compiled.

---

### Post by John.Michael.Kane on 2006-04-04
your better off just getting the latest kernel that has the suport files you need, and compiling from that. it seems like a lot of work just for one patch.

---

### Post by grendel_khan on 2006-04-04
Compiling one file and executing two module-fiddling commands seems like less work to me than recompiling an entire Linux kernel and installing another set of modules, identical to the other set except for one single module that's been changed.

The patch I have is not integrated into the latest kernel. There's [archaic instructions](http://www.faqs.org/docs/kernel/x204.html) about how to compile kernel modules independently of compiling the entire kernel--just using the installed kernel headers--and they look pretty simple. I can't believe that it would be less work to recompile and install an entirely different kernel version for a single module.

---

### Post by grendel_khan on 2006-04-04
There's also a previous thread about this (which didn't really reach a conclusion) at

[http://ubuntuforums.org/showthread.php?t=142467&highlight=xpad](http://ubuntuforums.org/showthread.php?t=142467&highlight=xpad)

---

### Post by grendel_khan on 2006-04-04
This is the beginning of the errors that I get when I try to compile the modded xpad.c in the kernel source tree I just got from the package repository:
```
$ make xpad
cc     xpad.c   -o xpad
In file included from xpad.c:69:
/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/)"
xpad.c:73:24: error: linux/slab.h: No such file or directory
```

---

### Post by grendel_khan on 2006-04-05
I ended up grabbing the Ubuntu kernel sources for my current kernel, going into drivers/usb/input, moving xpad.c to xpad.c.old and dropping in the modded version I got. I then went to the kernel root, did **make oldconfig**, then **make modules**. xpad.ko was in drivers/usb/input; I did a **rmmod xpad**, followed by **insmod ~/bin/xpad.ko ddr_mode=1**. **jstest --event /dev/js0** shows that the driver is behaving as expected. (Though I'm getting notes in the syslog that it uses the deprecated usb_unlink_urb() function instead of the preferred usb_kill_urb(), which I think must have been a change from 2.6.11, which this driver was for, to the current 2.6.12 which I'm using. Still, the driver appears to work.

I still wish I could have just compiled it individually without doing an entire 'make modules'. But at least I got it to work.

(If anyone knows how I could have avoided the trouble, please tell me; I'd still like to know.)

---

### Post by &amp;)ky#)^ on 2006-10-27
I know that this thread is old, but I'd just like to say 'thank you'.  My xbox s-type controller was very crippled due to the very old version of xpad.c that is included with teh vanilla kernel.  With this awesome module update, it's working great now.  Thanks.

---

### Post by grendel_khan on 2006-10-28
You'll be even happier to find that the patch has *finally* made it into the mainline kernel.

[http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=deb8ee43a23d48116cb23eb8dd1de2348efb1e80](http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=deb8ee43a23d48116cb23eb8dd1de2348efb1e80)

Which means it'll probably be in Edgy+1, unless someone can convince the backport team to bring the patch to Edgy.

---

### Post by binary1230 on 2006-11-28
Hey guys

I wrote that patch originally.  That patch will be officially in kernel 2.6.19 which is due out in the next few weeks I hope.  I hope it helps, I always found the xpad DPAD thing to be so annoying.

There were a few weird versions of that patch before it made it to the kernel in its nice, final form.

The right version to use is this one:
[http://einsteinsbreakfast.com/demos/xpad-patch.diff](http://einsteinsbreakfast.com/demos/xpad-patch.diff)

The others had a few minor compile errors that you could hit.  If you use the older versions, but you've got a working xpad module from it, everything should run just fine though.

One thing.

That patch has a list of known dance pad USB id's which it uses to figure out if your controller is a dance pad.

If it knows about your controller, there's no need to pass ddr_mode=1 (OLD WAY) or dpad_to_buttons=1 (NEW WAY).  If your dance pad doesn't work without those options, it means the driver doesn't have your USB id's.

If that's the case, send me the output from the 'lsusb' command so I can add your dance pad to the list.

Thanks! Let me know if you've got any problems.
-Dom

---

### Post by binary1230 on 2006-12-03
**REAL UPDATED ANSWER**

Linux kernel 2.6.19 is out! Upgrade to that and your DDR pad should work correctly out of the box.

If it still doesn't then do this to force it to map the DPAD to buttons instead of axes:

modprobe xpad dpad_to_buttons=1

If that works then please do 'cat /proc/bus/usb/devices' and send me the output (binary1230-at-yahoo-dot-com) so I can add your dance pad USB id's to the list of DDR pads.

-Dom

---

