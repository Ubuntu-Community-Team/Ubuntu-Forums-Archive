---
title: "option on boot - no DMA for CDROM drive?"
date: 2006-05-14
forum: General Help
---

### Post by biriuk on 2006-05-14
Hello,

Anyone knows if there is an option to boot Ubuntu 5.10 without DMA for DVD drive or into a CD-ROM / DVD compatibility mode ?

b++

---

### Post by louis_nichols on 2006-05-14
Sure. Do this:
1. Backup the file we'll be editing:

```
sudo cp /etc/hdparm.conf /etc/hdparm.conf.backup
```

2. Open it for editing
```
sudo gedit /etc/hdparm.conf
```

3. Add an entry like this (assuming /dev/hdc is the device you're interested in)

```
/dev/hdc {
	dma = off
}
```

4. Save it and reboot.

---

### Post by biriuk on 2006-05-14
ah, I should've specified.
I am looking for a way to disable DMA from the first linux boot, in order to be able to install ubuntu.

b++

---

### Post by biriuk on 2006-05-14
I tried (with no luck) using the following:

boot: live pci = noacpi
boot: live acpi=off noacpi
boot: live irq poll
boot: live nolapic noapic

---

### Post by louis_nichols on 2006-05-14
I think it's

live dma=off

or, after booting the kernel, use:

sudo hdparm -d0 /dev/hdc

---

### Post by biriuk on 2006-05-14
thank you for your help. tried that but it didn't worked.

BUT:

I found the solution in kubuntu forum post:

[http://ubuntuforums.org/showthread.php?t=82017](http://ubuntuforums.org/showthread.php?t=82017)

---
Also there is a bug that discusses this: 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=16901](https://bugzilla.ubuntu.com/show_bug.cgi?id=16901)

The trick is:
live cdrom-detect/cdrom_hdparm=-d1
---

---

