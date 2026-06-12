---
title: "Ubuntu won't boot."
date: 2010-11-14
forum: General Help
---

### Post by galexy19 on 2010-11-14
When I try to boot my computer with Ubuntu 10.10 installed on the harddrive it takes me directly to the GRUB boot loader screen after the BIOS loads. I choose the appropriate kernel to boot with and I get the follow error message on a black screen:

```

run-init: /sbin/init: No such file or directory
######  Kernel1 panic - not syncing: Attempting to kill init!
######  Pid: 1, comm: run-init Not tainted 2.6.35-35-generic #37-Ubuntu
######  Call Trace:
######  [<####>] ? printk+0x2d/0x35
######  [<####>] forget_original_parent+0x2e4/0x2f0
######  [<####>] ? call_rcu+0xd/0x10
######  [<####>] exit_notify+0x13/0x170
######  [<####>] do_exit+0x17c/0x340
######  [<####>] ? redirected_tty_write+0x0/0x90
######  [<####>] sys_exit+0x18/0x20
######  [<####>] syscall_call+0x7/0xb

```When I try to boot using the live media, it takes me to the purple screen that says 'Ubuntu 10.10' and that its loading, and then it takes me to a black screen which follows:
```

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

```Ok,
- I've check my ram and reseated it.
- I check my BIOS setting and they seem to be correct.
- I've tried to load other kernel from the Grub menu, and none of them work.
- I tried reburning my live cd  media several times, and that didn't work.
- I tried to boot live cd from another cdrom drive, and that didn't work.
- I tried booting live media from a usb drive written using 'unetbootin' , when I set the BIOS to load from usb, it didn't recognise the boot and took me to the GRUB screen.
- What else? Oh.... tried using other live cds like Fedora 13 and Knoppix (no go).
- Tried resetting GRUB loader using tools like 'Supergrub' and 'Rescatux' , no sir.
- Called a friend, told me to post to this forum.

Hopefully someone can help?

*emachine desktop , 2700+ AMD Anthlon 2.0 ghz , 250 gb hardrive (Ubuntu 10.10 entire drive no partitions), 512 ram , dvd/cd-dr , dvd-rw, motherboard graphic and sound card.  *

---

### Post by dark.generic on 2010-11-14
have you tried another hard drive?

---

### Post by sohlinux on 2010-11-14
strange Input/output error Can not mount the filesystem even in the live cd. how old is the computer?

---

### Post by |{urse on 2010-11-14
Have you swapped out your data cables? Sata/Ide?

---

### Post by galexy19 on 2010-11-14
>           have you tried another hard drive?Tried unplugging my main hd and booting from a secondary external hd I use as storage with the live cd. I got the same error with the live cd as I had before.

>          strange Input/output error Can not mount the filesystem even in the live cd. how old is the computer?
The computer is about 6 yrs old. 

>           strange Input/output error Can not mount the filesystem even in the live cd. how old is the computer?     
No, I haven't changed my data cables recently.

---

### Post by sohlinux on 2010-11-14
when did you last have windows and was it working ok?

I wonder since your pc is 6 years old it may be worth trying Lubuntu or Xubuntu which are a bit lighter

with the  Input/output error it makes me wonder if you have some hardware issue

did you ever try to install to a usb stick,

---

### Post by galexy19 on 2010-11-14
Windows was probably installed on this computer 6 years ago. I got it used and it came without and operating system. It could very well be the hardware, I willing to replace some parts, just don't really understanding what could be broken.   
- I tried booting live media from a usb drive written using 'unetbootin'  , when I set the BIOS to load from usb, it didn't recognise the boot  and took me to the GRUB screen.

---

### Post by sohlinux on 2010-11-14
> **galexy19 said:**
> Windows was probably installed on this computer 6 years ago. I got it used and it came without and operating system. It could very well be the hardware, I willing to replace some parts, just don't really understanding what could be broken.   
- I tried booting live media from a usb drive written using 'unetbootin'  , when I set the BIOS to load from usb, it didn't recognise the boot  and took me to the GRUB screen.

normally you will get some beeps for hardware errors and if you can boot to the bios and all looks good then I dont know, older laptops may not be able to boot from usb sticks. try windows xp on it just to ascertain if it works at all.

---

### Post by galexy19 on 2011-03-23
Lol, so it turns out the reason I couldn't boot was because the cdrom drive I was trying to boot live cd from was having problems. I unplugged that, and made my slave the master. The live cd booted then.

```
 fdisk /dev/sda1 (or what ever sh#%%y drive you have)  
```

push 'y' to all errors. 
Reboot, should have fixed bad sectors on drive!

---

