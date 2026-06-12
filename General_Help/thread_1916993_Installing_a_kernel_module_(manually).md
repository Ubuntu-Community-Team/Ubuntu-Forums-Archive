---
title: "Installing a kernel module (manually?)"
date: 2012-01-29
forum: General Help
---

### Post by Shancial on 2012-01-29
I am trying to get battery charging thresholds to work on lubuntu 11.10 using a workaround a person posted to the arch linux wiki. 

[https://wiki.archlinux.org/index.php/Tp_smapi#2nd_Option](https://wiki.archlinux.org/index.php/Tp_smapi#2nd_Option)

The problem is that I can't get acpi_call kernel module to install.

Can someone guide me through the install? I used these instructions to try to install it myself:

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

After doing sudo insmod acpi_call.ko, no confirmation comes up and when I do sudo modprobe acpi_call, it says that it doesn't exist. Next I tried to copy the acpi_call.ko file to /lib/modules/3.0.0-12-generic/kernel/drivers/acpi but it also doesn't work.

I am a linux newbie and just tried everything I could find on the net, but I didn't find anything close to my situation that isn't expert-talk

Thanks!


EDIT: My laptop is Lenovo x121e. I didn't find anything hardware related requirements so I assumed it works universally

---

### Post by pbrane on 2012-01-29
First were did you get tp-smapi? Did you install from the ubuntu repos? There is a package called *tp-smapi-dkms* that probably has the compiled module in it. There is one called *tp-smapi-source* also. If you compiled the source against your current kernel it should load. The kernel module *acpi_call* has to be compiled on the working kernel to load correctly. You should be able to run
```

tail -f /var/log/syslog

```
to see system messages as you load/unload the driver. *dmesg* should work too but is not real-time.

*insmod* should work but *modprobe* will attempt to load any modules needed as well.

Offhand I don't know which directory the driver should be installed to. The one you attempted to install to is probably correct. In the past I had developed a kernel module that worked from the directory I built it in.

---

### Post by Shancial on 2012-01-29
I asked for help on the lubuntu irc channel, and a helpful user directed me to the bumblebee repository, from which I could install acpi-call-tools, and I successfully modprobed acpi_call (no errors came up atleast)

I installed tp-smapi-dkms through ubuntu repos. (it doesn't work on this laptop, but it is a requirement for the perl script I am trying to use.)

tail -f /var/log/syslog prints out:


Jan 29 14:46:53 minirusty kernel: [ 9994.224654] acpi_call: Calling \_SB.PCI0.LPC.EC.HKEY.BCSS
Jan 29 14:46:53 minirusty kernel: [ 9994.224679] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
Jan 29 14:49:05 minirusty kernel: [10126.057189] thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x01:0x00)->0xfffffff0
Jan 29 14:49:05 minirusty kernel: [10126.057203] thinkpad_ec: initial ec test failed
Jan 29 14:49:18 minirusty kernel: [10139.315780] acpi_call: Calling \_SB.PCI0.LPC.EC.HKEY.BCSS
Jan 29 14:49:18 minirusty kernel: [10139.315807] acpi_call: Cannot get handle: Error: AE_NOT_FOUND


Obviously running the tpacpi-bat perl script doesn't work. It prints out the same thing as syslog.

EDIT: tp_smapi itself doesn't support the new Lenovo motherboards, that's why I am trying to get this workaround to work. I don't think compiling tp-smapi from source for my kernel would help that, wouldn't it?

---

### Post by pbrane on 2012-01-29
> **Shancial said:**
> ...
EDIT: tp_smapi itself doesn't support the new Lenovo motherboards, that's why I am trying to get this workaround to work. I don't think compiling tp-smapi from source for my kernel would help that, wouldn't it?

Probably not. Have you looked at the latest kernel changelog? Maybe there is support for the newer Lenovo system boards now. You can check at [http://www.kernel.org/]("http://www.kernel.org/") although a quick search of the latest changelog does not yield anything. Building and installing a new kernel is not a trivial undertaking but isn't too hard - see this [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")
You can use the latest stable kernel tarball instead of *git clone*-ing the mainline. I built and use the 3.2.2 kernel on Xubuntu 11.10.

I don't have a Thinkpad so my help is very limited.

---

### Post by Shancial on 2012-01-29
> **pbrane said:**
> Probably not. Have you looked at the latest kernel changelog? Maybe there is support for the newer Lenovo system boards now. You can check at [http://www.kernel.org/]("http://www.kernel.org/") although a quick search of the latest changelog does not yield anything. Building and installing a new kernel is not a trivial undertaking but isn't too hard - see this [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")
You can use the latest stable kernel tarball instead of *git clone*-ing the mainline. I built and use the 3.2.2 kernel on Xubuntu 11.10.

I don't have a Thinkpad so my help is very limited.



I will look into that, but I think the main problem is ACPI_CALL. It gives me the error AE_NOT_FOUND I posted above. Is there anything I can do?

---

### Post by pbrane on 2012-01-29
> **Shancial said:**
> I will look into that, but I think the main problem is ACPI_CALL. It gives me the error AE_NOT_FOUND I posted above. Is there anything I can do?

Have you seen this?
[https://bbs.archlinux.org/viewtopic.php?id=127210]("https://bbs.archlinux.org/viewtopic.php?id=127210") it may help.

I found this too.
[http://ubuntuforums.org/showthread.php?t=1894892]("http://ubuntuforums.org/showthread.php?t=1894892")

and this (looks promising)
[https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management]("https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management")

---

### Post by Shancial on 2012-01-29
> **pbrane said:**
> Have you seen this?
[https://bbs.archlinux.org/viewtopic.php?id=127210]("https://bbs.archlinux.org/viewtopic.php?id=127210") it may help.

I found this too.
[http://ubuntuforums.org/showthread.php?t=1894892]("http://ubuntuforums.org/showthread.php?t=1894892")

and this (looks promising)
[https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management]("https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management")

I have seen the top 2. I also checked out TLP form the bottom link, but it seems to use tp_smapi, which doesn't work on this laptop. There is another way to get battery thresholds to work, since I've seen it working on a similar laptop without tp_smapi.

The arch forum one does have a solution yes, but I am so noob in linux stuff that I don't know what they are talking about. I don't know how to put that info to use, since I don't even have an optimus card and my error message is different

---

