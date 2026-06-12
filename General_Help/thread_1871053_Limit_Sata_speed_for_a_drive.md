---
title: "Limit Sata speed for a drive?"
date: 2011-10-28
forum: General Help
---

### Post by listerdl on 2011-10-28
Anyone know how to do that?

Long story short, my machine can NOT allow faster speeds but ubuntu keeps trying and failing to set faster speeds and enters into this perinnial loop.

Id rather tell the kernel to relax and set the speed to 1.5 gbp/s

thanks

---

### Post by listerdl on 2011-10-29
Is this a distro whereby you can limit the SATA speed manually?

Am I wasting my time trying to work this one out? I have had zero reply from any forum - google searches amount to nothing.

Bottom line, I dont think you can limit or set a limit to SATA speeds right? Thanks...

:confused:

---

### Post by dcstar on 2011-10-30
> **listerdl said:**
> Anyone know how to do that?

Long story short, my machine can NOT allow faster speeds but ubuntu keeps trying and failing to set faster speeds and enters into this perinnial loop.

Id rather tell the kernel to relax and set the speed to 1.5 gbp/s

thanks

Check your hard drives, some have a jumper setting to limit the SATA connection rate.

Also:

[http://serverfault.com/questions/120098/linux-kernel-option-to-set-sata-disk-to-udma-133-1-5gbps](http://serverfault.com/questions/120098/linux-kernel-option-to-set-sata-disk-to-udma-133-1-5gbps)

---

### Post by Nixarter on 2011-10-30
Well, are you sure it's failing?  I trouble-shot a transfer fail "issue" that turned out to just me being impatient.  I was transferring large files to and from external drives.  They said they were transferring faster then I usually can on other OS's... so I assumed it was working.  Then the dialog boxes would disappear, but when I tested the files they weren't complete.  Then I looked and when I transferred files, the hdd light stayed on.  Eventually I waited l waited long enough and the files were actually transferring at a much slower rate.

But you might not be as impatient as I...

---

### Post by listerdl on 2011-10-30
@nixarter - its not failing as such just that the kernel is forcing the SSD to operate at a rate faster than the mobo will allow.

@dcstart - We could be onto a winner here!

The instructions on that link you enclosed were:

[COLOR="DarkGreen"]Add this

libata.force=1.5
to your boot options and it will force libata to 1.5Gbit. You can also force DMA modes etc, check out kernel-parameters.txt in your kernel documentation directory (or online say here) > This takes you to the "Kernel Parametres"[/COLOR]

My next question! How do I edit the libata! Thanks!

---

### Post by listerdl on 2011-10-30
OK I answered my own question: to find libata I did locate libata and it worked. Now next thing is to locate which one of these files is associated with the "boot options"

Any ideas?

# locate libata
/lib/libatasmart.so.4
/lib/libatasmart.so.4.0.3
/usr/lib/ssl/engines/libatalla.so
/usr/share/apport/package-hooks/libatasmart4.py
/usr/share/doc/libatasmart4
/usr/share/doc/libatasmart4/README
/usr/share/doc/libatasmart4/changelog.Debian.gz
/usr/share/doc/libatasmart4/copyright
/usr/src/linux-source-2.6.38/Documentation/DocBook/libata.tmpl
/usr/src/linux-source-2.6.38/arch/ia64/include/asm/libata-portmap.h
/usr/src/linux-source-2.6.38/arch/powerpc/include/asm/libata-portmap.h
/usr/src/linux-source-2.6.38/drivers/ata/libata-acpi.c
/usr/src/linux-source-2.6.38/drivers/ata/libata-core.c
/usr/src/linux-source-2.6.38/drivers/ata/libata-eh.c
/usr/src/linux-source-2.6.38/drivers/ata/libata-pmp.c
/usr/src/linux-source-2.6.38/drivers/ata/libata-scsi.c
/usr/src/linux-source-2.6.38/drivers/ata/libata-sff.c
/usr/src/linux-source-2.6.38/drivers/ata/libata-transport.c
/usr/src/linux-source-2.6.38/drivers/ata/libata-transport.h
/usr/src/linux-source-2.6.38/drivers/ata/libata.h
/usr/src/linux-source-2.6.38/include/asm-generic/libata-portmap.h
/usr/src/linux-source-2.6.38/include/linux/libata.h
/var/lib/dpkg/info/libatasmart4.list
/var/lib/dpkg/info/libatasmart4.md5sums
/var/lib/dpkg/info/libatasmart4.postinst
/var/lib/dpkg/info/libatasmart4.postrm
/var/lib/dpkg/info/libatasmart4.shlibs
/var/lib/dpkg/info/libatasmart4.symbols

---

### Post by matt_symes on 2011-10-30
Hi

Open a terminal and type

```
sudo nano /etc/default/grub
```Look for the lines..
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```and change them to 

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=DarkGreen]libata.force=1.5[/COLOR]"
GRUB_CMDLINE_LINUX="[COLOR=DarkGreen]libata.force=1.5[/COLOR]"
```Press ctrl + o to save and ctrl + x to exit.  Then type

```
sudo update-grub
```Reboot your PC. Check the command line by typing

```
cat /proc/cmdline
```Kind regards

---

### Post by listerdl on 2011-10-30
@matt-symes - thanks VERY much - your advice helped from this error repeated twice a second in the log viewer:


```
limiting SATA link speed to 1.5 Gbps
ata4: hard resetting link
```

So we are making progress! Unfortunately the error I now get is this twice every second:

```
ata2: exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen
ata2: irq_stat 0x00000040, connection status changed
ata2: SError: { CommWake DevExch }
ata2: hard resetting link
ata2: SATA link down (SStatus 0 SControl 310)
ata2: EH complete
```

This is repeated in a constant loop over and over.

I know the cause of this - its just trying to figure out how to get the kernel or the grub to stop seeking to "hard resetting link"

(The cause is that Panasonic toughbooks, my machine, do not install fans due to them possibly breaking down - so to prevent heat spikes they remove all moving fans BUT limit all SATA to SATA I).

The machine works fine but I cant help thinking that there is something "wrong" with the above error being looped twice a second in the log viewer!!

Thanks again and fingers crossed you can advise!

---

### Post by dcstar on 2011-10-31
Your profile says 10.04, if that is correct then try and upgrade to a release using a later kernel that may be more compatible with your hardware.

---

