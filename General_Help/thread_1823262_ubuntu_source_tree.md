---
title: "ubuntu source tree"
date: 2011-08-11
forum: General Help
---

### Post by vibuntu99 on 2011-08-11
I am trying to create local ubuntu-karmic source tree, so that I could compile it for ARM machine. All the steps involved are still very new to me which I haven't sort out at this point. I've got the following command working, and it has downloaded the linux kernel tree in local drive.

git clone git://kernel.ubuntu.com/ubuntu/linux-2.6 [passed]

git clone --reference linux-2.6 git://kernel.ubuntu.com/ubuntu/ubuntu-karmic.git
[failed with messages:Cloning into ubuntu-karmic...
fatal: The remote end hung up unexpectedly
] 

then I tried another one command,
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-karmic.git also failed with the same messages.

However, I tried with the command
 git clone git://kernel.ubuntu.com/ubuntu/ubuntu-maverick.git, it works.

Hence, I believe, it has something to do with karmic. It is probably no longer in repos. If it is true, how do I get it? If it is false, anyone know why?

Any comments would be appreciated.

Cheers!
vibuntu

---

### Post by gordintoronto on 2011-08-12
Karmic is old. I suggest to skip forward to 10.04 or 11.04.

You can browse to packages.ubuntu.com to see what is available.

---

### Post by vibuntu99 on 2011-08-12
The reason for using Karmic is because the ARM machine I have takes only ARMV6 instruction sets,and Karmic is the last version of Ubuntu that is compiled using ARMV6 instructions. 


I checked on the [http://packages.ubuntu.com/](http://packages.ubuntu.com/), strangely it doesn't have Karmic 9.10.

---

### Post by CatKiller on 2011-08-12
> **vibuntu99 said:**
> 
I checked on the [http://packages.ubuntu.com/](http://packages.ubuntu.com/), strangely it doesn't have Karmic 9.10.

Karmic has reached its end of life and is no longer supported.

I'm confused; if you're compiling yourself, why does it matter which architecture others have compiled for?

---

### Post by vibuntu99 on 2011-08-12
You are absolutely right, that is why I am after only the right version, Karmic Koala which was coded with ARMV6 instruction sets. The higher releases use ARMV7 instruction sets.

---

### Post by CatKiller on 2011-08-12
No, I still don't understand. The architecture is chosen at compile-time. You haven't compiled yet. The fact that there aren't binaries already available to you for later versions doesn't matter because you aren't using binaries anyway.

---

### Post by vibuntu99 on 2011-08-12
I think you are right. I would need specify the option to use ARMV6 instructions. Do you know how to do to that?

---

### Post by vibuntu99 on 2011-08-12
Yep, I think I manage to compile by specifying -march=armv6 in CFLAGS. The Maverick I downloaded is being compiled while I am writing this for about 5 mins. Hopefully it go through till the end. This is just  testing of the setup. My intention is to achieve an xubuntu image for the S3C6410 machine.

Cheers!

---

