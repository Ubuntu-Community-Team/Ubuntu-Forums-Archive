---
title: "linux-image-2.6.32-31-generic Error"
date: 2011-06-29
forum: General Help
---

### Post by mobius129a on 2011-06-29
I'm reposting this in General Help from the Installation and Upgrades section, because it may be a more general problem with my system. Any help much appreciated!

Kernel version: 2.6.32-30-generic
Distro: Ubuntu 10.04

Whenever I install a new package or upgrade, I get the following error:

```

     Setting up linux-image-2.6.32-31-generic (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 14: quiet: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-2.6.32-32-generic (2.6.32-32.62) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-32-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 14: quiet: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-32-generic; however:
  Package linux-image-2.6.32-32-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.32.38); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            No apport report written because MaxReports has already been reached
                                                                                                                                                                                Errors were encountered while processing:
 linux-image-2.6.32-31-generic
 linux-image-2.6.32-32-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```
The error does not however prevent packages from being installed  nor does it prevent packages from being upgraded. However, I'd like to  find the root of the problem and how I can resolve it.

TIA.

---

### Post by Habeouscorpus on 2011-06-29
sudo dpkg --configure linux-image-generic ?

---

### Post by mobius129a on 2011-06-29
Ok, I tried that and that brought up a message stating that  linux-image-2.6.32-32-generic needs to be configured. So...

```

sudo dpkg --configure linux-image-2.6.32-32-generic
Setting up linux-image-2.6.32-32-generic (2.6.32-32.62) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-32-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 14: quiet: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 linux-image-2.6.32-32-generic

```Do I need to update to grub 2!? I've avoided updating grub from v1 because I felt there was little need and I had read somewhere that it can cause problems to dual-booting machines.

thanks for the reply btw.

---

### Post by pqwoerituytrueiwoq on 2011-06-29
using grub legacy on lucid with the 2 newest kernels without issue
 so i bout changing boot-loaders would help
what happens when you rub [FONT=Courier New]sudo update-grub[/FONT]

---

### Post by mobius129a on 2011-06-29
I get:
```
/etc/default/grub: 14: quiet: not found
```

---

### Post by pqwoerituytrueiwoq on 2011-06-29
it seems to be think you are using grub 2 not legacy grub
[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)
i would make sure grub 2 is not installed and or reinstall legacy grub that link my help you

---

### Post by gmargo on 2011-06-29
Please show the content of the **/etc/default/grub** file.  You appear to have a typo in it.

---

### Post by mobius129a on 2011-06-29
Content of **/etc/default/grub**:```
# If you change this file, run 'sudo update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0

# If you want to always default to the previously selected option, uncomment these
#GRUB_DEFAULT=saved
#GRUB_SAVEDEFAULT=true

#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;ipv6.disable=1 quiet splash&#8221;
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```.I'm on a different machine so will **pqwoerituytrueiwoq**'s suggesting of installing grub legacy. I made a mistake in saying that it was grub v1: it's actually grub v2.  :oops: How could you tell from the posts I gave above?

---

### Post by drs305 on 2011-06-29
Don't install Grub legacy yet.

The error in /etc/default/grub is with the type of quotation marks you used. Use 'straight' quotes:
> 
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;ipv6.disable=1 quiet splash&#8221;


Open the file for editing:
```
gksu gedit +14 /etc/default/grub
```

Replace the line with the following, then run "sudo update-grub".

> GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

This will at least solve the grub error which is being issued when the various post-installation scripts are run.

Note: We know it's Grub 2 because Grub legacy didn't have an /etc/default/grub file.

---

### Post by mobius129a on 2011-06-29
Ok, I'll try that.

---

### Post by mobius129a on 2011-06-30
Ok, that worked. There are no problems at all now. Thanks.

---

