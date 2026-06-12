---
title: "grub4dos halt doesn't work"
date: 2010-05-29
forum: General Help
---

### Post by josephellengar on 2010-05-29
Anybody here know anything about grub4dos?  I'm building myself a multiboot flash drive using grub4dos and one of my commands on the menu, obviously, is shutdown.  This should be simply "halt" but every time I launch that command, or if I type it into the grub4dos command line, the computer locks up and I have to do a hard reboot.  Any idea why this might be?  It's not critical, but it is annoying.

---

### Post by josephellengar on 2010-06-08
bump.

---

### Post by josephellengar on 2010-06-09
bump.  Does anybody have any idea?

---

### Post by john newbuntu on 2010-06-09
Yes I have the same problem but I never use the halt option on my multiboot drive.  You could try "halt --no-apm" and see if that helps although I doubt it.  Also try "help halt" on the prompt and see if you find any other options.

Most times, I use a distro in the grub4dos menu and end up shutting down using the options in that distro (typically shutdown -h now).

I have noticed that the command "reboot" works though. But obviously that would reboot the comp.

---

### Post by josephellengar on 2010-06-09
> **john newbuntu said:**
> Yes I have the same problem but I never use the halt option on my multiboot drive.  You could try "halt --no-apm" and see if that helps although I doubt it.  Also try "help halt" on the prompt and see if you find any other options.

Most times, I use a distro in the grub4dos menu and end up shutting down using the options in that distro (typically shutdown -h now).

Yeah, I've tried --no-apm.  Did you make your drive using this: [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/) too?  Because I think that that might use an older version of grub4dos and that's why I'm having a problem, since that's what I used.

---

### Post by john newbuntu on 2010-06-09
Yes I did it from that site a while back.  I used a newer version of syslinux and installed it on MBR directly since their default installation did not pick up my external USB drive.  The rest of it was just copy stuff from that site on to the active fat32 partition of my drive.

---

### Post by tinybit on 2010-06-10
halt uses APM to shut down the computerr. many machines do not support APM halt protocol.

halt --no-apm will dead lock the machine, with a infinte loop of the jmp instruction.

the latest 0.4.5 series supports execution of external command(sometimes called "out command"). so you may try the g4d_off command, which is downloadable from chenall's grub4dos site. g4d_off uses ACPI to shut down the machine.

---

### Post by josephellengar on 2010-06-10
> **tinybit said:**
> halt uses APM to shut down the computerr. many machines do not support APM halt protocol.

halt --no-apm will dead lock the machine, with a infinte loop of the jmp instruction.

the latest 0.4.5 series supports execution of external command(sometimes called "out command"). so you may try the g4d_off command, which is downloadable from chenall's grub4dos site. g4d_off uses ACPI to shut down the machine.

Thanks!  I downloaded it, but I'm not all that well versed in g4d. Would the command that I add to my menu.lst just be:
(assuming that the g4d_off command is in the root directory of the drive)

```

title Shutdown
/g4d_off

```

Thanks.

On a sort of unrelated note, I noticed that I'm using version 0.4.4 of g4d. Does this version have this capability?  And also, if I just replace the grub.exe that syslinux is chainloading with the newer one, will that update properly?

---

### Post by josephellengar on 2010-06-10
> **rossholley said:**
> Thanks!  I downloaded it, but I'm not all that well versed in g4d. Would the command that I add to my menu.lst just be:
(assuming that the g4d_off command is in the root directory of the drive)

```

title Shutdown
/g4d_off

```

Thanks.

On a sort of unrelated note, I noticed that I'm using version 0.4.4 of g4d. Does this version have this capability?  And also, if I just replace the grub.exe that syslinux is chainloading with the newer one, will that update properly?

Can't figure out how to use the g4d_off thing.  When I put in the above entry, it just doesn't show up in my menu.  Did anyone here get it to work?

---

### Post by tinybit on 2010-06-13
of course you need the 0.4.5 series. yes, you may just update your grub.exe to the 0.4.5 (latest).

and yes, it is /g4d_off

---

### Post by josephellengar on 2010-06-13
> **tinybit said:**
> of course you need the 0.4.5 series. yes, you may just update your grub.exe to the 0.4.5 (latest).

and yes, it is /g4d_off

When I tried that:
```

title Shutdown
/g4d_off

```

the option did not show up on the grub menu.  Everything else did.  Why would that be?  I tried it with the g4d_off command still in a tarball in the root directory and with the command uncompressed in the root directory.

---

### Post by tinybit on 2010-06-13
> need the 0.4.5 series

Which grub4dos version? Are you still using 0.4.4? 

Can you enter command line and input your commands there?

try

/g4d_off

and press the Enter key.

If still failed, try

find --set-root /g4d_off

and then

/g4d_off

if you are using it in a menu, append a dummy boot command to it:

title shut down
find --set-root /g4d_off
/g4d_off
boot

---

### Post by josephellengar on 2010-06-14
> **tinybit said:**
> Which grub4dos version? Are you still using 0.4.4? 

Can you enter command line and input your commands there?

try

/g4d_off

and press the Enter key.

If still failed, try

find --set-root /g4d_off

and then

/g4d_off

if you are using it in a menu, append a dummy boot command to it:

title shut down
find --set-root /g4d_off
/g4d_off
boot

I tried all of the following commands:
```


title Shutdown attempt 1
find --set-root /g4d_off
/g4d_off
boot

title Shutdown attempt 2
find --set-root /g4d_off
/g4d_off

title Shutdown attempt 3
find --set-root /g4d_off
boot

title Shutdown attempt 4
find --set-root /g4d_off
boot

```

Attempt 3 was unselectable.  Attempt 4 said kernel must be loaded first.  Attempts 1 and 2 said 
```

Error 27: Command not found

```

I also tried plugging all of the commands into the commandline manually, with the same results.

---

