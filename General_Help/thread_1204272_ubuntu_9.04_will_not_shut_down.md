---
title: "ubuntu 9.04 will not shut down"
date: 2009-07-04
forum: General Help
---

### Post by DiegoTe5 on 2009-07-04
Hi there,
I have just upgraded to 9.04 (my pc is new and came with 8.10) and it just won't shut down. When i try to shut it down it seems okay until it boots up again for no apparent reason. I've searched a lot now, and a lot of people seem to have pcs that hang when shutting dow but mine dones't hang, it boots up again.
At first, it said something like
```

'will now halt
 *halt: unable to iterate IDE devices: no such file or directoy'.

```
Ater a bit of search i found a "solution": to modify /etc/modules and write:
```

apm power_off=1

```
and /boot/grub/menu.lst:
```

title		Ubuntu 9.04, kernel 2.6.27-7-generic
uuid		7903513f-1c22-4ff4-a78d-2f0026a49db8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7903513f-1c22-4ff4-a78d-2f0026a49db8 ro [COLOR="Red"]acpi=off apm=power_off[/COLOR]
initrd		/boot/initrd.img-2.6.28-13-generic

```
Now the halt message isn't there when i try to shutdown from gnome. But it still appears when shutting down from the options menu at the login screen.

Also, at startup, it says something like 
```

ata4: ACPI get timing mode failed (AE 0x0000d)

```

I'm completely lost at this point. Any help?

Thanks in advance.

---

### Post by Soul-Sing on 2009-07-04
Are these threads helpful for you:
[http://ubuntuforums.org/showthread.php?t=987699](http://ubuntuforums.org/showthread.php?t=987699)
[http://ubuntuforums.org/showthread.php?p=6983391](http://ubuntuforums.org/showthread.php?p=6983391)

---

### Post by DiegoTe5 on 2009-07-04
No, it really doesn't. It doesn't hang, it just restarts instead of shutting down.
Also, after the first "solution" (apm power_off=1) the halt error doesn't show anymore, but it still restarts.

---

### Post by markharding557 on 2009-07-04
try> sudo haltin a terminal

---

### Post by DiegoTe5 on 2009-07-04
doesn't help. still shuts down and restarts on its own. also, i can't suspend or hibernate the pc, it wakes up immediately

---

### Post by synapsys on 2009-07-04
```
sudo poweroff -n
```

---

### Post by DiegoTe5 on 2009-07-04
nothing, it keeps rebooting.

---

### Post by flyingsliverfin on 2009-07-04
try 

sudo shutdown -P now

but from your other errors i dont think it will work

---

### Post by DiegoTe5 on 2009-07-05
nothing :(

---

### Post by flyingsliverfin on 2009-07-05
hm.... you might want to check the logs, even though i have no idea were they are kept myself

---

### Post by DiegoTe5 on 2009-07-06
look for what in what logs???

---

### Post by DiegoTe5 on 2009-07-06
edit & bump:-?

---

### Post by markharding557 on 2009-07-06
he means log viewer in system>adminisration you might find some clues in there

---

### Post by DiegoTe5 on 2009-07-06
well, this is what I've found in syslog. I have no idea whatsoever on how to read log files, much less on what kind of 'clue' i should be getting from this.
```

* scsi2 : ata_piix
* scsi3 : ata_piix
* ACPI Exception (exoparg2-0444): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFF) is beyond end of object [20080926]
* ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.IDE1.GTM_] (Node f6c157c8), AE_AML_PACKAGE_LIMIT
* ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.IDE1.CHN1._GTM] (Node f6c15708), AE_AML_PACKAGE_LIMIT
* [COLOR="Magenta"]ata4: ACPI get timing mode failed (AE 0x300b)[/COLOR]
* ata3: SATA max UDMA/133 cmd 0xf0e0 ctl 0xf0d0 bmdma 0xf0a0 irq 19
* ata4: SATA max UDMA/133 cmd 0xf0c0 ctl 0xf0b0 bmdma 0xf0a8 irq 19

```
I have found no log mentioning the halting problem.

thanks for your time.

bump, bump, bump!

---

### Post by flyingsliverfin on 2009-07-08
in worst case scenario u could reinstall ubuntu... but there must be a way to fix this!

---

### Post by c0mput3r_n3rD on 2009-07-08
try:
 ```
sudo shutdown -h now
```

---

### Post by c0mput3r_n3rD on 2009-07-08
better yet, try 
```

sudo shutdown -h now >> shutdownLog.txt

```
and:
```

sudo shutdown -h now 2>> shutdownErrors.txt

```

then check to see if their is anything in those files

---

### Post by DiegoTe5 on 2009-07-08
> **c0mput3r_n3rD said:**
> better yet, try 
```

sudo shutdown -h now >> shutdownLog.txt

```
and:
```

sudo shutdown -h now 2>> shutdownErrors.txt

```

then check to see if their is anything in those files


Nothing in either of them :-?

---

### Post by icetnet on 2009-07-14
Just as a matter of course... Check the BIOS to see if it is set up to "Restore power to previous state" in case of power failure. Each BIOS has their own verbiage for this. I have seen the BIOS misinterpret the ACPI shutdown signal as a loss of power and thus reboot. Just a thought.

---

### Post by DiegoTe5 on 2009-07-14
> **icetnet said:**
> Just as a matter of course... Check the BIOS to see if it is set up to "Restore power to previous state" in case of power failure. Each BIOS has their own verbiage for this. I have seen the BIOS misinterpret the ACPI shutdown signal as a loss of power and thus reboot. Just a thought.

You, sir, are a genius! There was this option "wake on LAN from S5" or something similar set to "turn on". Don't really know what it does, but changing it to "stay off" did the trick. You deserve a cookie.

Thanks for all guys =)

---

### Post by flyingsliverfin on 2009-07-15
was not expecting it to be something with the BIOS lol

---

