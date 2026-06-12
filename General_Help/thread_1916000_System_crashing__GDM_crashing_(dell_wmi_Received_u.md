---
title: "System crashing / GDM crashing (dell_wmi: Received unknown WMI event (0x11))"
date: 2012-01-27
forum: General Help
---

### Post by d3ngar on 2012-01-27
Hi,

It seems that my system - or better the desktop - is crashing randomly because of an error with a kernel module.

I don't really know how to figure out which is the offending module, as I don't know much about modprobe, but a colleague said that it's a problem with the kernel...

When I look at dmesg, the last entries before the desktop crashes are a few lines of:

```
dell_wmi: Received unknown WMI event (0x11)
```

I see that I get a lot of these errors, but only sometimes it will cause the desktop to become unresponsive.

Any hints you can give me?

Thanks,

Chris

---

### Post by d3ngar on 2012-02-03
Sadly this thread has seemingly not created any reply. Shame really.

If anyone has a similar problem. I managed to disable this module in the Kernel, but that didn't solve the problem. The laptop was working a lot faster though.

To disable a kernel module have at the list of modules loaded:
> lsmod
You can grep that:
> lsmod | grep SOMETHING

Lastly, you can create your own blacklist by simply creating a file in the folder:
> /etc/modprobe.d/
I created one named blacklist-custom. Then simply write the module to blacklist in the file and Bob's your uncle.

Good luck!

---

### Post by d3ngar on 2012-02-03
1

---

### Post by j0lle on 2012-05-03
I'm having similar issues...
my system crashes once shortly after booting. after that, no issues.

I posted this bug upstream as well: [https://bugs.freedesktop.org/show_bug.cgi?id=49220](https://bugs.freedesktop.org/show_bug.cgi?id=49220) 
as you can see in the logs that message pops up once in a while.

Do you have any issues with VGA output?

---

