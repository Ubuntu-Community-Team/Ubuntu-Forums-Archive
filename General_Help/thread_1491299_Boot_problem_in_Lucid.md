---
title: "Boot problem in Lucid"
date: 2010-05-23
forum: General Help
---

### Post by asai on 2010-05-23
Hi,
I have installed (fresh) 10.04 on a HP laptop.
It worked like a charm at first, but after an update it didn't boot.
It hangs on splash screen.
I got it to work when I edited the boot line and entered nomodeset at the end. When it booted the x server ran at low resolution. I got an option to restart X, and everything looked fine.
However, at reboot the same problem again.
Did the same procedure. When the system came up, I edited /etc/default/grub
Now the system comes up every time, but I still have to restart X at every boot.
Any suggestion on this issue?

---

### Post by asai on 2010-06-09
This is still an issue.
Any suggestion to resolve this?

---

### Post by anubis75 on 2010-06-09
> **asai said:**
> Hi,
I have installed (fresh) 10.04 on a HP laptop.
It worked like a charm at first, but after an update it didn't boot.
It hangs on splash screen.
I got it to work when I edited the boot line and entered nomodeset at the end. When it booted the x server ran at low resolution. I got an option to restart X, and everything looked fine.
However, at reboot the same problem again.
Did the same procedure. When the system came up, I edited /etc/default/grub
Now the system comes up every time, but I still have to restart X at every boot.
Any suggestion on this issue?
  U did not specify the system ur running!!!

---

### Post by philinux on 2010-06-09
@asai, Can you provide system specs?

---

### Post by asai on 2010-06-09
> **asai said:**
> Hi,
I have installed (fresh) 10.04 on a HP laptop.

;)

---

### Post by asai on 2010-06-09
> **philinux said:**
> @asai, Can you provide system specs?
HP Elitebook 8530p
Lucid 10.04

---

### Post by krazyd on 2010-06-11
> **asai said:**
> HP Elitebook 8530p
Lucid 10.04

video card?

---

### Post by Jakiejake on 2010-06-11
> **krazyd said:**
> video card?

Look it up!
ATI Mobility Radeon™ HD 3650 with 256 MB of GDDR III video memory
[http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/321957-321957-64295-3740645-3955549-3782310.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/321957-321957-64295-3740645-3955549-3782310.html)

---

### Post by krazyd on 2010-06-12
try editing the boot command and remove the word ```
splash
``` from the end

---

### Post by asai on 2010-06-14
Here is my /etc/default/grub:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
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
```
There is no "Splash" here... :-\"

---

### Post by krazyd on 2010-06-15
what happens when you remove 'nomodeset' (just leave the string blank ="")?

don't forget to run 'sudo update-grub' after editing /etc/default/grub

---

### Post by asai on 2010-06-16
It works!

This is what I did:
First I tried krazyds suggestion, but the same error appeared.

Then I ran this command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by zazootheparrot on 2010-10-14
Hello there,

I have an ubuntu 10.04 Lucid Lynx running on a Sony Vaio VGN-SZ740.  During the past week I've had a problem with the operating system  booting. It happened after I did the usual update of the system using  the update manager.
It's worth mentioning that I have a Linux/ Windows 7 dual boot but they  all worked fine before. Here's what I see in the GRUB page when I start  my computer:
```
GNU GRUB version 1.98-ubuntu 7
Ubuntu, with linux 2.6.32-25-generic
Ubuntu, with linux 2.6.21-25-generic (recovery mode)
Ubuntu, with linux 2.6.21-24-generic
Ubuntu, with linux 2.6.21-24-generic (recovery mode)
Ubuntu, with linux 2.6.21-23-generic
Ubuntu, with linux 2.6.21-23-generic (recovery mode)
Ubuntu, with linux 2.6.21-21-generic
Ubuntu, with linux 2.6.21-21-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest console 115200)
Windows 7 loader (on/dev/sda1)
```After I choose the first one (as I always did), I get the following:
```
Ubuntu 10.04.1 LTS ava-laptop tty1
ava-laptop login .. [129.736043] tpm_tis 00:09: tpm_trasmit :tpm_send:  error 42 94967234
```and then it takes more that 3 minutes for ubuntu  to come up!!!

I would we grateful if anyone could could help me solve this issue,

Thank you in advance

---

