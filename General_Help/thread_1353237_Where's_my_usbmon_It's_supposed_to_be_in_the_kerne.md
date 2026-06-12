---
title: "Where's my usbmon? It's supposed to be in the kernel!"
date: 2009-12-12
forum: General Help
---

### Post by OfNoNation on 2009-12-12
I've been researching how to auto-switch a USB GPRS modem which is recognised as a CD-ROM until it's ejected, when it becomes a modem again.
Everything pointed towards installing USB-Modeswitch, which I did.  However, because I have an obscure and unsupported Chinese (though labelled 'Vodafone MD950') modem, I have to use a USB sniffer to find some of the variables required by USB-Modeswitch (MessageEndpoint & MessageContent).
Everyone who's written anything about it says that 'usbmon' is all I need and it's actually built in to the Linux kernel..... YESSSSS!
Following the instructions posted by the masses I typed...

```
mount -t debugfs none_debugs /sys/kernel/debug


```and got the response...

```

mount: none_debugs already mounted or /sys/kernel/debug busy
mount: according to mtab, none is already mounted on /sys/kernel/debug

```... which seemed to be okay.
The next command is...
```
modprobe usbmon
```which resulted in...

```
FATAL: Module usbmon not found.
```... which I found a little scary.

Is usbmon included in the kernel?
If so, and considering that I've found no trace of anybody else having this problem, why am I getting reports of fatalities when I start to do something that the Linux world can do with ease?
I want my usbmon!  Can anybody tell me where to find it?

---

### Post by falconindy on 2009-12-12
Check in /lib/modules/`uname -r`/kernel/drivers/usb/mon/ for the existance of a 'usbmon.ko'. If its not there, the default Ubuntu kernel doesn't provide it. Chances are its not, if modprobe didn't find it.

In case you need to recompile, [this](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/) will get you started.

---

### Post by OfNoNation on 2009-12-12
Thanks for the quick response.
There is no /mon in that location and searching / for usbmon.ko produced no results.  So I guess I have to install the module usbmon.

I feel another headache coming on!

---

### Post by falconindy on 2009-12-12
> **OfNoNation said:**
> Thanks for the quick response.
There is no /mon in that location and searching / for usbmon.ko produced no results.  So I guess I have to install the module usbmon.

I feel another headache coming on!
Because it only takes me less than 10 minutes to compile a complete kernel, I always forget that you're able to compile a single kernel module without redoing the whole thing.

The link below looks like it should be of use.
[http://chinese-watercolor.com/nicholas/linux/kernel.html](http://chinese-watercolor.com/nicholas/linux/kernel.html)

---

