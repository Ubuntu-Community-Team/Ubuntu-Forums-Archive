---
title: "Weird issue with GRUB2 that causes it to hang"
date: 2010-09-14
forum: General Help
---

### Post by Renée Jade on 2010-09-14
OK guys I am having a pretty strange issue with my GRUB2. I'm going to try and give you all the info in the one post so please excuse its considerable length.


I have Ubuntu 9.10 x86_64 and Windows 7 Home Premium x86_64 installed on the one hard drive. The motherboard is a GIGABYTE GA-X58A-UD7.


Boot loading is handled by GRUB2

```
renee@renee-desktop:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)

```I've changed the names of the files in my /etc/grub.d/ directory so that they look like this

```
renee@renee-desktop:/etc/grub.d$ ls
00_header        09_os-prober  20_memtest86+  README
05_debian_theme  10_linux      40_custom

```And my /usr/share/grub/default/[COLOR=Black]grub[/COLOR] file looks like this

```
renee@renee-desktop:/usr/share/grub/default$ cat grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

...

```All of which means that my boot menu displays Windows 7, then the Linux kernels then mem-tests. The default menu entry is Windows 7 and it boots automatically after 10 seconds. That is all fine.


BUT, if I select the first of the Linux kernels and hit enter without a delay of about 10 seconds, maybe longer, the whole thing hangs up and I have to hard-reboot. All I see on the screen when this happens is a flashing cursor in the top left corner.


Has anyone else had this problem? Does anyone know how to fix it, even by hacking in a forced delay on commencing boot after hitting enter at the boot menu?

---

### Post by dcstar on 2010-09-15
> **Renée Jade said:**
> OK guys I am having a pretty strange issue with my GRUB2.
.........
**I've changed the names of the files in my /etc/grub.d/ directory so that they look like this**
...........
Has anyone else had this problem? Does anyone know how to fix it, even by hacking in a forced delay on commencing boot after hitting enter at the boot menu?

So what happens when you put the system files you changed back to the way they are supposed to be?

---

### Post by coffeecat on 2010-09-15
> **Renée Jade said:**
> I've changed the names of the files in my /etc/grub.d/ directory so that they look like this

Why? Anyway, have you made sure the ones that you want to include in grub.cfg are executable and the ones to ignore are non-executable?

> **Renée Jade said:**
> And my /usr/share/grub/default/[COLOR=Black]grub[/COLOR] file looks like this

```
renee@renee-desktop:/usr/share/grub/default$ cat grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

...

```

I'm fairly certain that you should be editing /etc/default/grub, not /usr/share/grub/default/grub. I believe the usr file is a reference one. Whatever, if you have an uncommented GRUB_HIDDEN_TIMEOUT line, that *might* be the problem. This below is the same section of my Lucid /etc/default/grub, which is the Ubuntu default, and it works just fine. Check your /etc/default/grub.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by Renée Jade on 2010-09-15
> **dcstar said:**
> So what happens when you put the system files you changed back to the way they are supposed to be?

Nothing. Sorry, I should have said that to begin with. The problem was there all along. This hack is fine and recommended to anyone who wants their Windows install at the top of the list. I just thought I'd include all GRUB related information.


> **coffeecat said:**
> Why? Anyway, have you made sure the ones that you want to include in grub.cfg are executable and the ones to ignore are non-executable?


Yes

> **coffeecat said:**
> 
I'm fairly certain that you should be editing /etc/default/grub, not /usr/share/grub/default/grub. I believe the usr file is a reference one. Whatever, if you have an uncommented GRUB_HIDDEN_TIMEOUT line, that *might* be the problem. This below is the same section of my Lucid /etc/default/grub, which is the Ubuntu default, and it works just fine. Check your /etc/default/grub.


I haven't uncommented anything in that file. I probably should have used one in /etc/ but whatever. Anyway, none of these alterations are causing the issue.

---

### Post by oldfred on 2010-09-15
Flashing cursor is normal as it starts to boot. Not booting is not.

Have you tried the recovery mode?

You can also hit e for edit on the grub menu and remove quiet splash so you can see the process of booting. Usually the last line or two on the screen relates to the problem.

Many problems lately seem to be related to video issues. What video card do you have.

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

---

### Post by Renée Jade on 2010-09-16
> **oldfred said:**
> Flashing cursor is normal as it starts to boot. Not booting is not.

Have you tried the recovery mode?

You can also hit e for edit on the grub menu and remove quiet splash so you can see the process of booting. Usually the last line or two on the screen relates to the problem.

Many problems lately seem to be related to video issues. What video card do you have.

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0


Thank you kind Sir. The video cards may be the issue. I've got two Radeon HD5850s in this machine and they are running a *HD5870* BIOS, which is a bit of a hack job too (I'm not really afraid to try scarcely documented tweaks on my computer :P). I can't remember if this issue arose before or after I flashed the BIOSs on the GPUs. Hmmm. I will have a look at what my options are in some of the finer points of GRUB configuration, run some more experiments and try to find out exactly where it hangs up. 

I'd like to just get the source code, find the service routing for 'Enter', and insert a few billion do-nothings at the start of it. But I don't think that is a viable option for me.

---

