---
title: "Help with Oracle VM virtualbox and Windows 7 64"
date: 2010-12-01
forum: General Help
---

### Post by Lancro on 2010-12-01
My windows 7 is 64 bits, I want to install it inside a virtual machine, I downloaded the latest version of VM for ubuntu maverick.

I setup the new VM, everything goes ok, but before starting de dvd to install windows 7 it tells me that the OS may not detect the 64 bits architecture, and tells me to enable at bios something called VT-x/AMD-V.

In my bios there is not such a thing, I havent seen that option in my life, so I press continue, and the windows 7 dvd tells me that my system is not 64 bits, my system is 64 bits, and it works out of VM, but I want it in linux so I can get rid of that partition, so I need help, what should I do?.

Thanks.

---

### Post by NCLI on 2010-12-01
> **Lancro said:**
> My windows 7 is 64 bits, I want to install it inside a virtual machine, I downloaded the latest version of VM for ubuntu maverick.

I setup the new VM, everything goes ok, but before starting de dvd to install windows 7 it tells me that the OS may not detect the 64 bits architecture, and tells me to enable at bios something called VT-x/AMD-V.

In my bios there is not such a thing, I havent seen that option in my life, so I press continue, and the windows 7 dvd tells me that my system is not 64 bits, my system is 64 bits, and it works out of VM, but I want it in linux so I can get rid of that partition, so I need help, what should I do?.

Thanks.
It sounds like the version of linux you're trying to run Virtualbox under isn't 64-bit. Can you post the output of this command?
```
uname -a
```

---

### Post by Lancro on 2010-12-02
```
Linux ubuntu 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux
```

And the windows 7 64 bits runs in partition, I want it in virtualbox, so the system is 64 bits, strange, isnt it?

Thanks.

---

### Post by leomeloxp on 2011-04-15
Hi,

I have the same problem in here and would like to know if anyone have found a solution for this. I'm able to set up my virtualbox okay, I'm under Maverick 10.10 64bits, but it doesn't allow me to install any 64bits OS on it. Not even Natty beta 64 it does.

If anyone can tell me what can I get to help you guys solve the problem, let me know and I'll do. I tried Googling around and doing some set ups but nothing worked so far.

Thanks in advance =]

---

### Post by linuxmaniack on 2011-04-16
It looks like your CPU does not look like it supports x64 OS's in visualization . I would recommend getting a AMD Athlon II x4 640. Its A quad core, and its under £100! (I got mine for £70! and its a quad!)

---

### Post by leomeloxp on 2011-04-16
I can't get a Quad Core XD I'm on a Dell Laptop, my processor is a Core 2 Duo P7550. Isn't it strange for my processor not to allow 64 bits system? Both my Windows and Ubuntu Maverick installs are 64 bits.

Anyway, thanks for the suggestion. I would think about it if it was possible XD

---

### Post by stephane.deom on 2011-05-13
In my BIOS it the options is called Virtualization Technology, not VT-x as Oracle VM virtualbox calls it...

---

