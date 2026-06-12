---
title: "Where to find Kernel Code Source?"
date: 2010-05-19
forum: General Help
---

### Post by sgsawant on 2010-05-19
I was trying to install VPN client for my Ubuntu 9.10 64-bit. During the installation process the terminal reads:

"Directory containing linux kernel source code** [/lib/modules/2.6.31-21-generic/build]**"

On that I pressed enter for the default option (in bold). After a few more steps I reached the following error:
Making module
sh: Can't open ./driver_build.sh
Failed to make module "cisco_ipsec.ko".

[/lib/modules/2.6.31-21-generic/build] is the location where the installer expects the kernel source to be (I am guessing). So unless I correct the terminal (by providing the location of the kernel source), I think I will keep on getting the same error message.

So to get the kernel source I visited: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

From there I copy pasted the command:
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)

Everything went fine, but even now I don't know if at all I have a kernel source and where it exists on my machine.

Any advice is appreciated.

Regards,

-sgsawant

---

### Post by dcstar on 2010-05-19
> **sgsawant said:**
> 
.........
Everything went fine, but even now I don't know if at all I have a kernel source and where it exists on my machine.

Any advice is appreciated.

Regards,

-sgsawant

/usr/src

---

### Post by amite on 2010-05-19
$ uname -r  
 this will show linux kernel release which is in use.

then u can find source code of kerenel at /usr/src/

---

