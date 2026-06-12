---
title: "Grub prompt help"
date: 2010-06-16
forum: General Help
---

### Post by thebigob on 2010-06-16
Hi all,

Managed to mess up my grub menu. (1.98 iirc)

Fixed a couple of things but now it goes to the grub prompt rather than the menu.

I can boot my windows partition doing:

```

grub:> root (hd0,1)
grub:> chainloader +1
grub:> boot

```

And to boot Ubuntu:

```

grub:> root (hd0,5)
grub:> configfile /boot/grub/grub.cfg

```

When in ubuntu if I do:

```

callum@callumlap:~$ sudo update-grub
[sudo] password for callum: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
callum@callumlap:~$ 

```

My question is how do I get it to use this as default rather than coming up with the grub prompt?

Thanks in advance for the help. Im happy to post any code that will help.

---

### Post by dcstar on 2010-06-16
> **thebigob said:**
> Hi all,

Managed to mess up my grub menu. (1.98 iirc)

Fixed a couple of things but now it goes to the grub prompt rather than the menu.
.........
My question is how do I get it to use this as default rather than coming up with the grub prompt?

Thanks in advance for the help. Im happy to post any code that will help.
What did you change in the /etc/default/grub file?

---

### Post by thebigob on 2010-06-16
> **dcstar said:**
> What did you change in the /etc/default/grub file?
Thanks for taking the time to look into this. I did not alter this file. However here it is:

```

callum@callumlap:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="splash"

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
callum@callumlap:~$ ^C
callum@callumlap:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="splash"

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
callum@callumlap:~$ 


```

---

### Post by john newbuntu on 2010-06-16
If you have only one HDD (/dev/sda), then install the grub to the MBR from the command line:
```
sudo grub-install /dev/sda
```
Otherwise make changes to the /dev/sdX appropriately.

Verify that grub identifies the /boot partition with:
```
grub-probe -t device /boot/grub
```
Should be /dev/sda5 in your case.  Reboot and check.

---

### Post by thebigob on 2010-06-16
> **john newbuntu said:**
> If you have only one HDD (/dev/sda), then install the grub to the MBR from the command line:
```
sudo grub-install /dev/sda
```Otherwise make changes to the /dev/sdX appropriately.

Verify that grub identifies the /boot partition with:
```
grub-probe -t device /boot/grub
```Should be /dev/sda5 in your case.  Reboot and check.

Worked perfectly.

Thank you so very much!

---

### Post by john newbuntu on 2010-06-16
welcome thebigob

---

