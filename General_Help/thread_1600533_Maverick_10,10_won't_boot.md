---
title: "Maverick 10,10 won't boot"
date: 2010-10-19
forum: General Help
---

### Post by MarkMyWord on 2010-10-19
I've recently upgraded from 10.04 to 10.10.  Everything was working well.  I was loving 10.10....until....I ran the update manager.  The system slowed right down and was non responsive.  Eventually I was able to click 'restart' and get it to start rebooting.

Now it is stuck part way through booting.

I get this message in a terminal screen:

Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/707f8c73-3d67-4629-8169-29ce9e44b999 does not exist.
Dropping to a shell!


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(intramfs) udevd[68]: worker [75] unexpectadly returned with status 0x0100

udevd[68]: worker [75] failed whle handling '/devices/pci0000:00/0000:00:1f .2/host0/target0:0:0/0:0:0:0/block/sda/sda1'


(initramfs)



I've typed 'reboot' several times and rebooted and keep ending up here.  At one stage I was able to choose what device I wanted to boot, so I chose diagnostic mode, but that stopped too.

And to think I've been gloating that Ubuntu is a Windows recovery tool.:confused:

Hope someone has some tips.

---

### Post by MarkMyWord on 2010-10-19
I've got it to GNU GRUB.  Not sure what to do from there.

I rebooted it, and entered command instead of trying to boot knowing boot would just fail.

BTW I'm a technical nuff nuff.  Did you notice?

---

### Post by sepo on 2010-10-19
Hi! I don't know 10.10, but I'd like to help :)
So....you have a terminal. Let's start with some command.

1st: list all your hard disks
```
ls /dev/disk/by-uuid/
```2nd: how ubuntu mount your drive(s)?
```
more /etc/fstab
```

---

### Post by MarkMyWord on 2010-10-19
Thanks for helping!

I entered ls /dev/disk/by-uuid/

and it returned a message; error: file not found

I then entered ls /dev   and got a list of things:

fd pts/ smh/ agpart apm_bios audio audio1 audio2......... dsp dsp1 dsp2........loop  loop1 loop2....  midi midi1 midi2.....  ram ram1 ram2..... etc

when I entered more /etc/fstab  it returned error: unknown command 'more'

I'm downloading 10.10 onto a USB using Windows right now in the hope that I'll be able to recover by booting from USB.  Hope it works!

---

### Post by MarkMyWord on 2010-10-20
It's not looking good for the meerkat.  Reinstall for me.  Next time I'll wait a while before upgrading.

---

