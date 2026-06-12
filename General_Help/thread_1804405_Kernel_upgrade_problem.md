---
title: "Kernel upgrade problem"
date: 2011-07-14
forum: General Help
---

### Post by srisharan on 2011-07-14
I did a system update today and included were kernel upgrades.However the kernel didnt upgrade properly.I get an error message and a notification to restart the system to update but when I start back up it is still not updates.Here is what happens when I run sudo apt-get upgrade

```
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic                                                                                                  
 *       vboxhost (4.0.10)...                                                                                                                                     [ OK ] 
 *       nvidia-current (270.41.06)...                                                                                                                            [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
/etc/default/grub: 25: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-10-generic; however:
  Package linux-image-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.10.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
 linux-image-generic
 linux-generic

```

Notice it says that **Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010**


Here is the line 1010 with the subsequent few lines (starting with 1010) in that file

>  system ("run-parts --verbose --exit-on-error --arg=$version " .
          "--arg=$realimageloc$kimage-$version " .
          "/etc/kernel/postinst.d") &&
            die "Failed to process /etc/kernel/postinst.d";
}


Now I dont know what to do with that.Can anyone help me here?
And I am on natty by the way

---

### Post by szal on 2011-07-14
srisharan,

Even earlier it says,
[INDENT][COLOR=Blue]/etc/default/grub: 25: Syntax error: newline unexpected[/COLOR]

[/INDENT]Please post your /etc/default/grub here.

---

### Post by srisharan on 2011-07-14
> **szal said:**
> srisharan,

Even earlier it says,
[INDENT][COLOR=Blue]/etc/default/grub: 25: Syntax error: newline unexpected[/COLOR]

[/INDENT]Please post your /etc/default/grub here.

Hmm,didnt see that.Here the file

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1024x800-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=>>1024x800-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

This is line 25 - ** GRUB_GFXMODE=>>1024x800-24<<**

---

### Post by szal on 2011-07-14
> **srisharan said:**
> Hmm,didnt see that.Here the file *[…]*

This is line 25 - ** GRUB_GFXMODE=>>1024x800-24<<**
There is your problem. That line is not properly formatted. I have no idea how to incorporate the colour depth here, but just for the resolution it’s supposed to read:
[INDENT][COLOR=Blue]**GRUB_GFXMODE=1024x800**[/COLOR]
[/INDENT][COLOR=Blue][COLOR=Black] 
HTH
[/COLOR][/COLOR]

---

### Post by srisharan on 2011-07-15
Yeah that worked.Thank you very much.Now marking this as solved

---

### Post by adempewolff on 2011-07-16
I had this same problem, and it looks like the fix worked.  Thanks!

Edit: actually, I spoke too soon.  fixing that line made the configuration complete successfully, but if I look carefully there are still grub errors, and the new kernel isn't actually added to the grub menu.  I'm going to create a new thread since this one is marked solved, but srisharen, you might want to double check that grub actually is booting you into the new kernel (2.6.38-10 vs. 2.6.38-8)

Edit: in case you still are having problems, here is my new post about the problems I am continuing to have: [http://ubuntuforums.org/showthread.php?t=1805641](http://ubuntuforums.org/showthread.php?t=1805641)

---

### Post by Paloseco on 2011-07-27
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798980](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798980)

# sudo chmod a-x /etc/kernel/header_postinst.d/nvidia-common
# sudo chmod a-x /etc/kernel/postinst.d/nvidia-common
Upgrade kernel headers and image.

---

