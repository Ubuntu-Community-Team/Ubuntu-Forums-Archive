---
title: "memtest86+ doesn't seem to be doing anything"
date: 2011-09-08
forum: General Help
---

### Post by njwatson32 on 2011-09-08
I installed some new RAM and wanted to run memtest86+. (It's v4.10.) I launched it from grub, but it doesn't seem to be doing anything. I have attached a photo of my screen. It does not look like [this]("http://www.memtest.org/pics/i875-big.gif"). I have a Lenovo Thinkpad T420 on which I dual-boot Windows 7 and Ubuntu 10.10. Both OS's were shut down (not hibernating) when I launched it (if it matters).

What am I doing wrong?

Thanks.

---

### Post by Grenage on 2011-09-09
Indeed; it doesn't seem to be doing a lot.  Working on the possibility that there's a problem with memtest, you could try either replacing the memtest image file (/boot/memtest86+.bin), or burn and boot from a bootable memtest ISO.

Both are available on the memtest website.

---

### Post by njwatson32 on 2011-09-10
> **Grenage said:**
> Indeed; it doesn't seem to be doing a lot.  Working on the possibility that there's a problem with memtest, you could try either replacing the memtest image file (/boot/memtest86+.bin), or burn and boot from a bootable memtest ISO.

Both are available on the memtest website.

Thanks, that worked. I downloaded a new binary and everything is fine.

---

### Post by Grenage on 2011-09-10
Glad to hear it. :)

---

### Post by mpollmeier on 2011-09-14
I had the same problem. Looking at the memtest release notes they added support for Intels "Sandy Bridge" in the latest 4.20 release, however Ubuntu 11.04 still ships the Memtest 4.10.

[http://www.memtest.org/#change](http://www.memtest.org/#change)

---

