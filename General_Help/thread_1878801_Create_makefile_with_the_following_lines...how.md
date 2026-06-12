---
title: "Create makefile with the following lines...how?"
date: 2011-11-10
forum: General Help
---

### Post by debiant on 2011-11-10
```
Step for step (I’m not sure if this the newest k10temp version!):

$ wget [http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin](http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin)
Hallo,
Trying to follow ther following...

$ mkdir k10temp && mv attachment.bin k10temp/k10temp.c

Now create the Makefile with following lines:

    obj-m := k10temp.o
    KDIR := /lib/modules/$(shell uname -r)/build
    PWD := $(shell pwd)
    default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
$ cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
$ depmod && modprobe k10temp
```

How do I "create a makefile with the following lines..."
Everyone else seems to just know this, it gets no explanation anywhere this fix appears on the web!  I tried Googleing makefile etc and its an extremely long document.  
I've tried guessing with stuff like make -f + the name of the module but I'm not getting anywhere.
I'm trying to fix a boot problem where it hangs because of an AMD CPU thermal throttle problem.  I will study the makefile document;  but if anyone can help me out so I can just use Ubuntu without the long wait for a bootup in the meantime, I'd really appreciate it.:)

---

### Post by debiant on 2011-11-11
Maybe everyone doesn't know this.  

So why write pages of "how to" and fail to describe this crucial step?

is this the famous clever/dumb balance at work?  Clever enough to write all that code I quoted above and no idea that you need to show how its used?

Any help will be very much appreciated.

:confused:

---

### Post by MG&amp;TL on 2011-11-11
When you say create a makefile with following lines...can you clarify a little? You want to have wget.....depmod in a makefile?

---

### Post by haresear on 2011-11-11
A makefile is just a text file. So you can use any text editor, e.g. gedit, type or copy/paste those lines, and save the file as 'Makefile'.

(The 'make' command will read the Makefile and do what it specifies. The Makefile should be in the directory where you issue the 'make' command.)

---

### Post by MG&amp;TL on 2011-11-11
Oh, gotcha. Never mind what I edited, being stupid, +1. :D

---

### Post by debiant on 2011-11-14
Thank you both for replying...

haresear, that is exactly what I needed to know.

I've created my Makefile and loaded the module I needed and now I boot up quicker with no errors!
You're explanation has also given me a bit more understanding of what I'm actually doing when I install packages and that is really cool.

Thank you!

=D>

---

