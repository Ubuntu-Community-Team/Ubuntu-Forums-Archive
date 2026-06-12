---
title: "Ubuntu Doubt"
date: 2011-01-06
forum: General Help
---

### Post by pedrobelo on 2011-01-06
Hi all, i'm new to Linux, i have one doubt and i hope you guys can help me out. I have Ubuntu and Windows XP on my pc.
Whenever an update on Ubuntu is done when booting my pc the board where i choose wich OS to use appears all my previous versions of Ubuntu.
Can i do anything to "erase" the previous versions of Ubuntu on that board?
Thank you

---

### Post by matt_symes on 2011-01-06
Hi

I assume you are talking about old kernels. Install Ubuntu tweak and remove them that way. Keep the current one and the last one in case there are any problems.

Kind regards

---

### Post by P1C0 on 2011-01-06
I found this article helpful in the past:
[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

But I strongly suggest to keep one extra linux kernel (the previous kernel from what you are currently running on).

---

### Post by pedrobelo on 2011-01-06
> **matt_symes said:**
> Hi

I assume you are talking about old kernels. Install Ubuntu tweak and remove them that way. Keep the current one and the last one in case there are any problems.

Kind regards

Matt, thanks for the quick reply, but like i told you i'm new in this OS. Dont know what Ubuntu tweaks are :confused:
Can you be a little bit more specific?
Thanks for your pacience

---

### Post by matt_symes on 2011-01-06
Hi

> Matt, thanks for the quick reply, but like i told you i'm new in this OS.

Yes. Sorry about that. You can install ubuntu tweak from synaptic package manager.

System->Administration->Synaptic package manager.

Search for "ubuntu tweak" without the quotes and install it.

Open a terminal and type 

```
ubuntu-tweak
```

to start it (or look under applications->system tools). Under package cleaner there is the option to remove old kernels.

Kind regards

---

### Post by mastablasta on 2011-01-06
Ubuntu tweak is a programme that ives a nice graphics interface for tweaking:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
 
Donwload the .deb file and double click it to start the instalation.

---

### Post by iponeverything on 2011-01-06
having the extra kernel's on the system does not affect anything. The amount of disk space they use is minute. If it is just having clean looking grub bootloader screen, I don't really understand why it matters -- but, it does seem to be an issue with a number of people.

---

### Post by pedrobelo on 2011-01-06
> **P1C0 said:**
> I found this article helpful in the past:
[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

But I strongly suggest to keep one extra linux kernel (the previous kernel from what you are currently running on).

Thank you P1CO

---

### Post by pedrobelo on 2011-01-06
> **matt_symes said:**
> Hi



Yes. Sorry about that. You can install ubuntu tweak from synaptic package manager.

System->Administration->Synaptic package manager.

Search for "ubuntu tweak" without the quotes and install it.

Open a terminal and type 

```
ubuntu-tweak
```to start it (or look under applications->system tools). Under package cleaner there is the option to remove old kernels.

Kind regards


Hi again Matt
Try to search ubuntu tweak on Synaptic package manager and didnt find it :(

---

### Post by howefield on 2011-01-06
> **pedrobelo said:**
> Hi again Matt
Try to search ubuntu tweak on Synaptic package manager and didnt find it :(

That's because it isn't there.. ;-)

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by matt_symes on 2011-01-06
Hi

Does the screen shot help?

Maybe it's in a different software source. I cannot look now though. I have to pop out. Others will help though

Kind regards

---

### Post by pedrobelo on 2011-01-06
> **howefield said:**
> That's because it isn't there.. ;-)

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Hi Howefield, thanks a lot, it worked.
@Matt thank you very much for you help

---

