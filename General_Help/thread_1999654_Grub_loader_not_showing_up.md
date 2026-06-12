---
title: "Grub loader not showing up"
date: 2012-06-08
forum: General Help
---

### Post by dagarshali on 2012-06-08
Hi,
I recently upgraded to 12.04 from 11.10. I also have windows installed on my system. All of sudden, the computer is booting windows directly instead of showing the grub screen to choose the OS. Any help as to how to fix this problem?

Best Regards,
Vishwa

---

### Post by wilee-nilee on 2012-06-08
> **dagarshali said:**
> Hi,
I recently upgraded to 12.04 from 11.10. I also have windows installed on my system. All of sudden, the computer is booting windows directly instead of showing the grub screen to choose the OS. Any help as to how to fix this problem?

Best Regards,
Vishwa

Boot a live ubuntu cd and run this command set. In home will be a results.txt, copy and paste all the text from it to a reply, highlight that text and click the # in the reply panel before clicking submit reply.
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by drs305 on 2012-06-08
I'd first try holding down the SHIFT key during boot to see if the GRUB menu appears. If it appears, does the Ubuntu option appear and will it boot?

If no menu shows up, it could be that GRUB is missing. This could be because BIOS is using a drive with the Windows bootloader.

I recommend booting a 12.04 LiveCD, installing and running Boot Repair. The link is in my signature line. If it can't repair your system, run the boot info script and post a link to the report.

---

### Post by ashikthomas on 2012-06-08
You need to reinstall grub boot loader. For that first boot the ubuntu CD. Then on terminal type

sudo grub-install /dev/sda

This may fix the problem.

---

### Post by wilee-nilee on 2012-06-08
> **ashikthomas said:**
> You need to reinstall grub boot loader. For that first boot the ubuntu CD. Then on terminal type

sudo grub-install /dev/sda

This may fix the problem.

You would have to chroot to the install, that will not work.

As well you do not know if the HD is sda.

---

