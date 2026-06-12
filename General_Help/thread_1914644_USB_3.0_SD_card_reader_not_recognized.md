---
title: "USB 3.0 SD card reader not recognized?"
date: 2012-01-24
forum: General Help
---

### Post by janmartin on 2012-01-24
Hi all,

I have tried two different USB 3.0 SD card readers. Both are recognized by Nautilus when plugged into a USB 2.0 socket.

As soon as I plug them into a USB 3.0 labeled socket, nothing happens. Worse, after a few seconds there is significant lag with the USB mouse.

Is USB 3.0 that new and unsupported?

What to do?

Thanks.

---

### Post by Double.J on 2012-01-24
> **janmartin said:**
> 
Is USB 3.0 that new and unsupported?

Not at all - don't worry about that, we've had USB3 support since at least 2009 :)

I'd say first things first - have a look in the bios for any kind of setting that could be affecting this. Both any USB options and media card options? 

Hope you find something!

---

### Post by Bobhuber on 2012-01-24
If your up to installing a newer kernel 3.2 (I think) and 3.3 (for sure) has support for USB 3.0.
And yes it's that new in the Linux world. The reason I say that is that I compile my own Kernels and noticed on the latest configuration file it was listed as (NEW)

Edit > I guess I stand corrected. According to what I read on Mr. Google 3.0 support was started in Sept 2009 with 2.6.31 Kernel. I have no idea why the make menuconfig file during a Kernel setup listed it as new .

---

### Post by Double.J on 2012-01-24
> **Bobhuber said:**
> . I have no idea why the make menuconfig file during a Kernel setup listed it as new .

I've pondered it a few times - I only knew it was working then because that's the Christmas I first installed Gentoo lol! I think sometimes the (NEW) *flag* is left on to help us with compiling - I'd hazard a guess that most computers running linux still have USB2 or earlier, so maybe it's to help us not to accidentally compile out USB2 and compile in USB3 (I'm not checking if that's possible) by accident? Personally I'd like to think people put a bit more effort into choosing options to be compiled in the kernel / as modules :D

I don't know - it's what I tend to assume when I use options with (NEW) at the end - I've tried googling, but of course the search engine gets bogged down with "new kernel" results. I've always assumed it's safe, as the Gentoo handbook uses examples of (NEW) options, but gives no warnings :)

---

