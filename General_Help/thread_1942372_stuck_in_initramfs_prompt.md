---
title: "stuck in initramfs prompt"
date: 2012-03-17
forum: General Help
---

### Post by ranjans89 on 2012-03-17
I was downloading movie and during that time computer screen went blank. To get out of this I restarted my computer but what I got after restarting is initramfs prompt.I tried many things to get out of this but anyone of them didn't work.I'm having dual boot PC.One more thing I'm not even able to boot from usb drive and getting same prompt.Is there any solution to this.If any please let me know.
Thanks in advance.
Given below is the link to image which shows the error.
[http://i.stack.imgur.com/Tetpf.jpg](http://i.stack.imgur.com/Tetpf.jpg)

---

### Post by matt_symes on 2012-03-17
Hi

Boot into a LiveCD/USB and try running fsck on the root partition.

If you need instruction on this, post back.

Kind regards

---

### Post by ranjans89 on 2012-03-19
It didn't work or I might be doing it wrong. Please tell be how should I do this.
Thanks

---

### Post by 2F4U on 2012-03-19
When the liveCD is booted, I would open a terminal and run

```
fsck /dev/sda1
```

---

### Post by raja.genupula on 2012-03-19
and use this too [http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)

---

### Post by ranjans89 on 2012-03-22
As I mentioned earlier I wasn't even able to boot from live USB. When I reboot the machine using live USB I got this message.
```
No init found. Try passing init= bootarg.
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
(initramfs)
```

---

### Post by matt_symes on 2012-03-24
Hi

> **ranjans89 said:**
> As I mentioned earlier I wasn't even able to boot from live USB. When I reboot the machine using live USB I got this message.
```
No init found. Try passing init= bootarg.
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
(initramfs)
```

Sorry. I missed that about the USB stick.

Do you have your USB stick as the first boot device. 

You can change it in the BIOS to make sure it is. 

You may also have a "quick select boot" option from the post screen. On my laptop, i need to press F8 or F10 to get this (i can never remember which one).

How did you create the USB stick ?

Kind regards

---

### Post by ranjans89 on 2012-03-24
Yes, I have USB as my first boot option. I created USB using UNIBOOTING on window 7.

---

### Post by theiron on 2012-03-25
I have a similar issue when creating Live-CD of ANY version of Ubuntu.  They never get past the Busybox error of "can not mout /dev/loop0 on /CDROM/casper/filesystem.squashfs".  I type 'exit' and more information is displayed about not finding files and not being able to chroot.

I can boot from this LIVE-CD from one of my laptops, but the machine that I really need it for is a desktop with a broken Windoze partition.  There is no booting it at all, albeit I did get a 9.10 Netbook Live-CD thru the partitioning of and installation.

I can not boot from USB, it is too old for that option in the BIOS.

I have created Live-CDs with ISORecorder and InfraRecorder in Windoze XP, as well as in Ubuntu 11.10 with Brasero and the CD-Writer that is built in, all meet with the same result, and CD-ROM that isn't bootable nor good for anything else.

I feel your pain, I've been wrestling with this for 3 weeks.

---

