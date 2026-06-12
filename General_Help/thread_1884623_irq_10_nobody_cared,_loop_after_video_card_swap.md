---
title: "irq 10: nobody cared, loop after video card swap"
date: 2011-11-21
forum: General Help
---

### Post by stg on 2011-11-21
Upgraded my video card, now my 9.04 will not boot.

I get a splash screen but then it loops a message 

IRQ 10: nobody cared try booting with irqpoll option

So in the GRUB2 screen I select my OS and push e, then add irqpoll after the splash...same thing

I know this is probably totally easy but searching is not finding me the answer, please help.

---

### Post by stg on 2011-11-21
been breaking on it

neither nomodeset nor irqpoll have any effect

any IRQ I force the video card to in BIOS comes back as "tainted" in the error loop

anybody?

---

### Post by stg on 2011-11-21
tried removing xorg.conf

same same

---

### Post by stg on 2011-11-22
Is it acceptable to bump ones threads here, if not I apologize.

I have installed a build of 10.04 on another partition, installed the restricted AMD driver and broke it also.  Recovery mode, nomodeset, nothing, hangs on the bootup splash animation.

Formatted the partition and have the 10.04 rebuilt, so at least I have an audio server, I am afraid to activate the video driver though.

---

### Post by b0b138 on 2011-11-22
whats the video card?

---

### Post by stg on 2011-11-22
Xfx hd 4650 1gb agp

---

### Post by b0b138 on 2011-11-22
[http://ubuntuforums.org/showthread.php?t=1444738](http://ubuntuforums.org/showthread.php?t=1444738)

---

### Post by stg on 2011-11-22
Hey, Thank you for the response.

Actually, I had seen that thread in my searches and it had my hopes all up.

The problem is that the AMD driver site no longer lists any linux option in the OS dropdown, which rather deflates one's hopes of performing the manual install.

If anyone has, or has a link to, the old 10.3 installer I am all ears.

---

### Post by b0b138 on 2011-11-23
> **stg said:**
> The problem is that the AMD driver site no longer lists any linux option in the OS dropdown, which rather deflates one's hopes of performing the manual install.

??? It did for me

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Theres also this page [http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx) But I see no reason the current version shouldn't work.

---

