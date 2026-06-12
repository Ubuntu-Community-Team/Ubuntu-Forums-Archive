---
title: "virtual serial port"
date: 2011-03-25
forum: General Help
---

### Post by Nigraffle on 2011-03-25
Hello everybody,
   A school project I'm working on requires us to have a computer with Ubuntu (host) on it hooked up via serial port to another computer (client) with MS-DOS.  I'd like to just virtualize the whole environment on my laptop, but it doesn't have a serial port.
   I have an image of the guest computer in VMware right now, but my laptop doesn't have any serial ports.  Is there any way I could have a program on my computer connect to a VMware virtual serial port, and send information that way?  I've been looking into socat, but I'm having a bit of a hard time understanding all the documentation.
   Thanks!

   -Adam

---

### Post by nice_like_rice on 2011-03-25
Netcat similar to socat but is very simple to use, have you looked into that?

It doesn't have bidirectional pipes but you could just use 2 instances I guess!

What exactly do you want to do with the data from the serial port?


:)

---

### Post by Nigraffle on 2011-03-25
It's an OS development class, so we're writing an operating system in C, compiling it for the target machine, then using a custom program developed by senior projects at the school to bootstrap the OS and run it.
The transfer and bootstrapping program we're running (SPEDE and FLAMES) don't really have a lot of documentation, so I'm trying to avoid messing with those too much.

I'll try netcat tonight, though, and hopefully come back with results.  Thanks!.

---

### Post by Nigraffle on 2011-03-27
Hmm... I was looking at netcat, and it seems that it only works for tcp and udp network connections.  The software I'm trying to use only works via serial port.

If I'm just not understanding how it actually works, please tell me, but it doesn't look like netcat is going to work for me.  Thanks, though.

---

### Post by nice_like_rice on 2011-03-27
Does this help?

[http://www.vmware.com/support/ws3/doc/ws32_devices3.html](http://www.vmware.com/support/ws3/doc/ws32_devices3.html)

---

### Post by Nigraffle on 2011-03-30
That looks like an awesome solution, however, I do not have access to a copy of VMware Workstation.  It's a little expensive for what I'm doing in this class :P

I ended up going through the socat documentation again, and got a virtual serial port to the VM working, however, this software package we're supposed to use for the class doesn't see it.

I think my easiest solution is going to be using 2 instances VMware player, one with a minimal Ubuntu install, and the other with the target environment, hooked up with a virtual serial port over a named pipe (VMware player can do that).  It's cleaner, but it may require more resources to do.

nice_like_rice's post (above) has a link to explain how to do that.

Thank you all for all your help

---

### Post by bouncingwilf on 2011-03-30
Is there any mileage in using a pair physical usb-> serial cables looped back to each other with a null modem cable? It's messy I know and hardly virtual but it's cheap and could be effective ( a "real" link).


Bouncingwilf

---

