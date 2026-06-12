---
title: "Dual boot, now windows won't open AutoNeoGrub.mbr"
date: 2011-01-28
forum: General Help
---

### Post by arsenalrule on 2011-01-28
Hi there,
I installed Ubuntu 10.10 Maverick Meerkat onto my Asus Eeepc 1215n notebook.
I previously had Windows 7 installed, and still do, but it wont boot anymore due to the error stated below.

Everything was working ok;
Grub 2 is installed and shows 
```
ubuntu, with linux 2.6.35-24-generic
ubuntu, with linux 2.6.35-24-generic (recovery mode)
memory test (memtest86+)
memory test (memtest86+, serial console 115200)
windows 7 (loader) (on /devsda1)
windows vista (loader) (on /dev/sda2)
```

Both win7 and ubuntu were dual booting fine. Then I was intrigued by the windows vista, so clicked to load vista, and it came up with the "recover, backup, exit" options, so I exited. Next time I tried to open win7 I receive this error:

```
windows failed to start. A recent hardware or software change might be
the cause. To fix problem:

1. insert our windows installation disc and restart your computer
2. choose your language settings and click "next"
3. click "repair your computer"

if you do not have this disc, contact your system administrator or
computer manufacturer for assistance.

File: \NST\AutoNeoGrub0.mbr
Status: 0xc000000f
Info: The selected entry could not be loaded because the application
is missing or corrupt.
```

I'm not at home at the moment, so cant back up my whole c:\ drive, so I don't really want to use the recover option from the vista partition. 

Does anyone know how I can fix this?
Thanks


Also Ive tried [using this recovery CD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD"), but I do not have a CD drive, and using unetbootin and universalUSB installer both just show the option of "default" with a 10second countdown when trying to boot the recovery CD from usb.

---

### Post by Mark Phelps on 2011-01-28
> **arsenalrule said:**
> Does anyone know how I can fix this?

Not specifically ... but the reference to NeoGRUB means that you had used EasyBCD in the past.  Recommend you check on the NeoSmart Technology forums.  They should be able to tell you how to either (1) fix this, or (2) remove EasyBCD and use GRUB instead.

---

### Post by arsenalrule on 2011-01-31
> **Mark Phelps said:**
> Not specifically ... but the reference to NeoGRUB means that you had used EasyBCD in the past.  Recommend you check on the NeoSmart Technology forums.  They should be able to tell you how to either (1) fix this, or (2) remove EasyBCD and use GRUB instead.

thanks mark, i asked at neosmart and they were very helpful :)
I am now able to boot windows, but then get a BSOD :( so I think I will have to reinstall windows

---

