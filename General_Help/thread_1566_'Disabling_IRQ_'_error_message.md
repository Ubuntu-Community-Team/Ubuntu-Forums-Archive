---
title: "'Disabling IRQ ' error message"
date: 2004-10-21
forum: General Help
---

### Post by lorax on 2004-10-21
I keep getting this message over and over - sometimes gnome won't start and the 'Disabling IRQ #193' messages scolls down the screen continually.

This is an extract from kern.log

Oct 22 00:51:57 localhost kernel: APIC error on CPU0: 60(60)
Oct 22 00:51:57 localhost last message repeated 12 times
Oct 22 00:51:57 localhost kernel: irq 193: nobody cared!

Oct 22 00:51:57 localhost kernel:  [__report_bad_irq+49/115] __report_bad_irq+0x31/0x73
Oct 22 00:51:57 localhost kernel:  [note_interrupt+76/111] note_interrupt+0x4c/0x6f
Oct 22 00:51:57 localhost kernel:  [do_IRQ+146/249] do_IRQ+0x92/0xf9
Oct 22 00:51:57 localhost kernel:  [common_interrupt+24/32] common_interrupt+0x18/0x20
Oct 22 00:51:57 localhost kernel:  [default_idle+0/38] default_idle+0x0/0x26
Oct 22 00:51:57 localhost kernel:  [default_idle+35/38] default_idle+0x23/0x26
Oct 22 00:51:57 localhost kernel:  [cpu_idle+29/50] cpu_idle+0x1d/0x32
Oct 22 00:51:57 localhost kernel:  [start_kernel+403/407] start_kernel+0x193/0x197
Oct 22 00:51:57 localhost kernel: handlers:
Oct 22 00:51:57 localhost kernel: [__crc_pm_idle+2732944/5541136] (usb_hcd_irq+0x0/0x4e [usbcore])
Oct 22 00:51:57 localhost kernel: [__crc_pm_idle+912058/5541136] (ide_intr+0x0/0x15d [ide_core])
Oct 22 00:51:57 localhost kernel: [__crc_pm_idle+4068206/5541136] (ohci_irq_handler+0x0/0x610 [ohci1394])
Oct 22 00:51:57 localhost kernel: Disabling IRQ #193



Any ideas what's causing this / how to fix it? Any help would be appreciated.


Cheers.

---

### Post by nkdb on 2004-11-07
Hi all,

I have today the same problem :

during all boot sequence, I have message :

IRQ 185 : Nobody care !
Disabling IRQ #185
...

and I can't start Ubuntu ...

Please help

More details ... :

* In recovery mode, I have this type of errors :
APIC error on CPU0 60(60)
* I have try to modify my BIOS config with disable :
Support APIC ACPI
=> error are not on IRQ 185 but on IRQ 11 ???

my Hardware :

- MB : Asus P4P800-E deluxe
- P4 2.8 C Multithread
- 2x256 DDRAM dual chanel
- VC : NV 5900 XT on AGP port x8

If that helps ...?

---

### Post by FirE-dRaGoN on 2004-11-07
try starting your system with the 'pci=noacpi' option (without quotes)

you can set this on GRUB menu... typing 'e' to edit the line that starts Ubuntu.

---

### Post by nkdb on 2004-11-08
Thank you for your answer.

i think i need more help with Grub use :

I accessed to Grub menu with "echap", I pressed "e"  and try to edit or create new line entries without success, with 2 instructions :

- pci=noacpi
- noirqdebug

I try to pass there instrucions on Grub command_line ("c") :

Error : unknow command !!!

Please help to use indicated command (how to use there with Grub ?)

Thank you so much

---

### Post by wallijonn on 2004-11-08
Do you have any USB devices connected to the mobo when installing the OS? If so, disconect them all and try again.

Failing that, try disabling USB in the BIOS before starting the install. (This may not work as disabling in the BIOS doesn't disable the device controller from being seen).

The other problem is that ASUS isn't known for providing Linux drivers to the Linux community.

---

### Post by fackamato on 2004-11-08
if you have a S-ATA hdd, enter bios, and change the sata settings so that S-ATA is **NOT** native. (but keep P-ata ports). this should do it.

(if it doesn't work still, fiddle with the settings :P)

---

### Post by nkdb on 2004-11-09
Yes, my modem is an USB modem .... I will try with disconnect it .... (I will install a ADSL modem/ router /switch so I will use Ether connection in the place of USB :) !)

I use an IDE DD.

Thank you for your help

---

### Post by ulrich on 2004-11-09
@nkdb

the file you want to edit is /boot/grub/menu.lst

and the line to edit should look like
```

kernel          /vmlinuz-YourKernelHere root=/dev/hdaX ro quiet splash pci=noacpi

```

you can edit this with an editor like vi or emacs or simply 'sudo gedit /boot/......' to have a 'gui'

hth

---

### Post by nkdb on 2004-11-15
hi all,

I would like to thank you for your help, I use now Ubuntu ....

I installed Modem / Router / Switch so I use Ether and not USB now ... and all is ok, I'm connecting ! :)

With "noirqdebug" instruction on boot comd line I resolve my problem on boot : "Disabling IRQ #185". But it's just a workaround and not a solution maybe. Could you help me to find what corresponding to IRQ #185 ? Does cmd exist for that ?
When I use "pci=noacpi" instruction on boot time, the IRQ problem number change to IRQ #11 ?

Thank you so much ...

---

### Post by nkdb on 2004-11-16
More details ...

at boot, with "noirqdebug", there is no problems ...

now, when I Shutdown Ubuntu, I have many errors as :

apic error on CPU0: 60(60)

(maybe both problem have no links ...?)

I read here : [http://www.webmasterworld.com/forum40/1124.htm](http://www.webmasterworld.com/forum40/1124.htm)
that I can use "noapic" to resolve the problem.

But I have 2 questions :

- If I use "noirqdebug" and "noapic", does my hardware could be damaged ?
- Does Linux kernel 2.6.8 (Ubuntu default) support my recent hardware (MB with many integrate chips, proc P4 multithread, DDR dual chanel, ...) ?

Thank you so much for your help ...

---

### Post by emil on 2005-02-15
Hi,

my S-ATA settings in BIOS were in Native mode, after I changed it to Legacy mode Ubuntu works like a clock! Thanks a million, this has been stopping me from using Ubuntu on my workstation for a couple of weeks!

/Emil


[QUOTE=fackamato]if you have a S-ATA hdd, enter bios, and change the sata settings so that S-ATA is **NOT** native. (but keep P-ata ports). this should do it.

(if it doesn't work still, fiddle with the settings :P)[/QUOTE]

---

### Post by Nobody on 2005-05-05
[QUOTE=fackamato]if you have a S-ATA hdd, enter bios, and change the sata settings so that S-ATA is **NOT** native. (but keep P-ata ports). this should do it.

(if it doesn't work still, fiddle with the settings :P)[/QUOTE] Man, I can't thank you enough for that bit of advice you gave there. My asus motherboard has been a pain with linux since my first installation of debian which, failed beautifully last year. Live cd's from different distributions including ubuntu and kubuntu have failed to load and when they did ran pitifully slow. Disabling this and disabling that, none but knoppix ran decently with reason still unknown to me. Thanks to you advice though, they run and shine while doing so. Looks like I can finally, start really playing with linux as the alternative os it is.

---

### Post by eger on 2006-08-21
I just want to say that changing the SATA/IDE controller to Legacy mode also fixed this issue for me on another linux distro. Doesn't look like a Ubuntu specific issue.

Thanks for the fix!

---

