---
title: "grub2 lists incorrect partitions"
date: 2010-10-19
forum: General Help
---

### Post by rocon on 2010-10-19
Hi

Grub2 is listing incorrect Windoze partitions on my dual boot system - it shows the loader to be on sda1 and the Recovery environment to be on sda2. They are in fact the opposite way round.  Which forum should I use to sort out this issue - or can anyone help here?

I do not need help to edit the wording on the menu itself.  I have already edited grub to do that so the menu reads correctly.  However the underlying file is still wrong.

Informatively, Gparted reports the correct partitions but grub2 and my user.log entries under 'linux 20microsoft result:' are incorrect.

Thanks

---

### Post by s.fox on 2010-10-19
Thread moved to General Help

---

### Post by coffeecat on 2010-10-19
I get the same inversion on my Sony laptop running Vista. On my  Acer/Win7 laptop with sda1 = recovery, sda2 = Win7 boot partition, sda3 =  Win7 C:, it's more surreal with grub telling me:

sda1 - Windows Vista (loader)
sda2 - Windows 7 (loader)
sda3 - Windows 7 (loader)

Tbh, it's not bothered me much. I'm sure there must be several bug reports in progress about it. In the meantime, and until the grub devs sort this out, you can re-configure grub to display the partitions correctly. However....

> **rocon said:**
> I do not need help to edit the wording on the menu itself.  I have already edited grub to do that so the menu reads correctly.

If you edited /boot/grub/grub.cfg, this will not stick and be overwritten next time there's a kernel upgrade. You need to make /etc/grub.d/40_custom executable and add you own entries and then make 30_os-prober non-executable. After which you run 'sudo update-grub'. More details here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Excuse me if you know that already.

Of course, that's only putting sticking plaster over a fault in grub. Perhaps someone else has a better fix.

---

### Post by rocon on 2010-10-19
Thaks coffecat.

Yes, I have already done the grub.d bit and supplied new 'LONGNAMEs' etc so I get a consistent boot but as you say it is sticking plaster.  I too am booting Vista/Ubuntu on a Sony laptop. My intrigue is that until your reply, I have not found a post about this issue so I'm not sure it is being addressed. Further, it is persistent across different ubuntu distros.

---

### Post by Quackers on 2010-10-19
Hmm I wonder if this is a Sony thing? Mine was the same until I followed drs305's guide to change the names.

---

### Post by coffeecat on 2010-10-19
> **Quackers said:**
> Hmm I wonder if this is a Sony thing?

Or perhaps only Vaio owners are aesthetically discerning enough to notice! :cool:

:wink:

---

### Post by Quackers on 2010-10-19
Undoubtedly sir :-) :-) :-)

---

### Post by rocon on 2010-10-19
Ok.

Since we all have the problem but none of us has the answer I have just added this to a similar bug filed on launchpad as bug #597793 in June this year. At the moment it has still not been assigned.

Further to the above, this appears to be a known Debian issue and would seem to be an error in /usr/lib/os-probes/mounted/20microsoft.

---

