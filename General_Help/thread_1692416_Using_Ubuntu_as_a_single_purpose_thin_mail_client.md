---
title: "Using Ubuntu as a single purpose thin mail client"
date: 2011-02-21
forum: General Help
---

### Post by Jazsun on 2011-02-21
I'm working on a project to create a very tiny barebones OS which would boot up, connect to the internet, and then ONLY display a mail client such as Thunderbird. This mail client would be previously configured with an email address and customized to be the only GUI present on the machine while locking the user into ONLY the mail client. 

**Hardware:**
This setup would have to run on a cheap, cost-effective thin client. I assume only a tiny processor (x86?), ~256MB of flash memory to support the OS and ~64MB of Ram would be necessary. These are just estimates at this point to provide a picture about the power of the system.

+ Does anyone have any recommendations for a tiny small purpose CPU or thin client combo?

**OS**
Would Ubuntu be a viable solution? Or would a different distro make more sense? I'd like to strip it of any and every necessary service outside the basic network TCP/IP configuration, USB port for keyboard/moust, VGA, and mail client use for sending/receiving mail from an HTTP email address (e.g. hotmail). I would like to have it boot fairly quick and straight into the customized mail client.

Is Ubuntu embedded or mobile where I should look for this stripped, quick boot, OS?


**Mail client**
I immediately thought Thunderbird would be the best solution provided the open source. Do you agree or is there any better way out there? Would it be fairly trivial to customize the Thunderbird GUI provided the help of a familiar programmer?

My goal is to keep the hardware/dev cost low, and have the system be very stable, and secure without requiring many patches/updates through a limited attack surface. 

**Resources**
If I decide to go the custom linux/ubuntu distro and Thunderbird route. Where would be the best place to find a developer who could take on some of these tasks?

Thanks all!

---

### Post by keithpeter on 2011-02-21
Hello Jazsun

[http://www.linutop.com/support/index.en.html](http://www.linutop.com/support/index.en.html)

I think your OS storage and ram specs might be a bit low judging by the linutop web site.

---

### Post by veggen on 2011-02-21
I must say I don't understand why would one make an OS that does a lot less that what a cheap phone does today, but ok.
From my understanding, you might want to take a look at Archlinux and maybe Puppy. I could be wrong though...

---

### Post by keithpeter on 2011-02-22
Hello All

Yes, Android had occurred to me as well as a small OS. There is also Slitaz.

I suppose this is for some kind of kiosk arrangement.

Cheers

---

