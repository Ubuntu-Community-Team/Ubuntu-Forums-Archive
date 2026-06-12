---
title: "(initramfs) prompt won't go away"
date: 2009-08-21
forum: General Help
---

### Post by jwmollman on 2009-08-21
I've searched and searched and searched on the Internet for a solution to this fix this. After installing Eeebuntu on my Asus EeePC, I rebooted just like it tells me. After I rebooted, the EeePC's loading screen comes up, then the Eeebuntu loading screen, but only for a second after I'm dropped to the (initramfs) screen with a blinking cursor.

BusyBox v1.1.3 (Debian 1:1.1.3-4) Built-in shell (ash)
> Enter 'help' for a list of built-in commands.

(initramfs)

I don't understand, because now when I try to boot up Eeebuntu, it will give me the same initramfs error. I tried booting another CD to see if the media was the issue. I tried to boot Tiny Core Linux and that successfully booted. If it was the Eeebuntu DVD, then why did it work the first time, and not the second time?

I'm currently whiping the computer to start fresh to see if that can really make me "start fresh."

---

### Post by dcstar on 2009-08-22
> **jwmollman said:**
> I've searched and searched and searched on the Internet for a solution to this fix this. After installing Eeebuntu on my Asus EeePC, I rebooted just like it tells me. After I rebooted, the EeePC's loading screen comes up, then the Eeebuntu loading screen, but only for a second after I'm dropped to the (initramfs) screen with a blinking cursor.

BusyBox v1.1.3 (Debian 1:1.1.3-4) Built-in shell (ash)
> Enter 'help' for a list of built-in commands.

(initramfs)

I don't understand, because now when I try to boot up Eeebuntu, it will give me the same initramfs error. I tried booting another CD to see if the media was the issue. I tried to boot Tiny Core Linux and that successfully booted. If it was the Eeebuntu DVD, then why did it work the first time, and not the second time?

I'm currently whiping the computer to start fresh to see if that can really make me "start fresh."

a) Probably because the install process created files that crash the boot-up.

b) Download the Ubuntu Netbook remix:

[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

---

### Post by bchurchill on 2009-08-22
There is almost definitely an error message we're not seeing here.  See if you can find it.  I've had this issue working with GRUB where root= has not been specified when starting the kernel, causing the kernel to be unable to mount / (which is obviously a pretty big problem).

From initramfs see if you can mount your filesystem using a command like 

```

mount /dev/... /

```

where the ... is the appropraite device file.  If you can't, that's probably your problem.

Otherwise, use a live CD to look at your boot loader (maybe grub?) to see how your kernel is being called, and if root= is being passed to it correctly 

in grub it should be a line in /boot/grub/menu.lst that looks something like

```
kernel /boot/vmlinuz..... root=/dev/sda... ro
```

---

### Post by ajmc on 2011-01-06
I have same error on my Lenovo s10 netbook.  I am using ubuntu 10.10 netbook version.

---

### Post by tholgutho on 2011-01-06
I have the similar error. I used double boot with bt4( backtrac - 4) for acuople moths ago, when computer booting and I select bt4 my computer (P5P800S - Asus Motherboard) in normal condition, but if I want to used Ubuntu I have a problem.
In the beginning of booting I have selected to recovery in lower kernel, I always found: 
target file system doesn't have /bin/init
No init found. Try passing init=bootag

Busy Box V1.13.3(ubuntu 1:1.13.3-1 ubuntu 11). Built in shell (ash)

(initramfs)

The my major problem is how I can take my documents in the /home/Documents directory that I really really needed. I have tray to make master-slave hard drives configuration, but still wont help my problem. After I mount that drive, I found an empty directory in /home. May be I am wrong or not understand Ubuntu. Would anybodies help me please.

Best Regard

---

