---
title: "Kernel Panic (Help me trace it!)"
date: 2011-08-25
forum: General Help
---

### Post by jshayden on 2011-08-25
[[IMG]http://jshayden.info/kp/kernel_panic_sm.jpg[/IMG]]("http://jshayden.info/kp/kernel_panic.jpg")
(Click image for larger version.)

The first kernel panic came about an hour after I plugged in and formatted a hard drive.  I checked the drive out using smartctl, and it seemed the drive had some issues.  So, I ditched the drive.  Thereafter, though, I got a kernel panic every 20 minutes.

I have since booted to a live CD and loaded down the CPU for 1.5 hours straight; I couldn't make it fail.  I also ran memtest+ and tried several RAM chips.  Anyway: I'm fairly convinced it is not hardware-related.

Any ideas?

Thanks, in advance.

---

### Post by debd on 2011-08-25
I think its related to the "panic_on_oom" feature. This variable (panic_on_out_of_memory) if set to 1 will panic the kernel evry now and then since cache files are always tried to be kept on the memory and the reported free memory is fairly small than what actually would be available.

run ```
cat /proc/sys/vm/panic_on_oom
```
if it returns '1', 
try ```
echo 0 > /proc/sys/vm/panic_on_oom
```

and see if the kernel still freaks out :)

---

### Post by jshayden on 2011-08-25
Thanks so much for the response.  Good idea, but, unfortunately, it seems panic_on_oom is already set to 0.

```

# cat /proc/sys/vm/panic_on_oom
0
```

---

### Post by debd on 2011-08-25
take a look here.. [http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/](http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/)

I dont have much time now.. :/

---

### Post by jshayden on 2011-08-26
> **debd said:**
> take a look here.. [http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/](http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/)

Thanks for the link.  My problem sure seems to be a soft panic.  The screen dump even has the "Oops" message.  Unfortunately, though, none of this makes it to /var/log/messages.  Hmmm.

---

### Post by fdrake on 2011-08-26
> **jshayden said:**
> Thanks for the link.  My problem sure seems to be a soft panic.  The screen dump even has the "Oops" message.  Unfortunately, though, none of this makes to to /var/log/messages.  Hmmm.

what about 
```

dmesg

```

---

### Post by jshayden on 2011-08-26
> **fdrake said:**
> what about 
```

dmesg

```

```

# dmesg | grep -i oops
#

```

:neutral:

---

### Post by jshayden on 2011-08-26
[[IMG]http://jshayden.info/kp/kp2_sm.jpg[/IMG]]("http://jshayden.info/kp/kp2_sm.jpg")
(Click for larger image.)

The dump is a bit different this time.  In case this provides any useful information ...

I have the machine running in recovery mode right now.  I'm going to see if it still panics.

Any more ideas?

Thanks!

---

### Post by debd on 2011-08-26
[http://www.av8n.com/computer/htm/kernel-lockup.htm](http://www.av8n.com/computer/htm/kernel-lockup.htm)

you may even update your kernel to a new one to see if it changes anything...

---

### Post by jshayden on 2011-08-26
> **debd said:**
> 
you may even update your kernel to a new one to see if it changes anything...

I did this.  I've tried 3 kernels, including those with PAE support and those without.

---

