---
title: "does installing ubuntu on a slave drive result in slower performance?"
date: 2010-08-14
forum: General Help
---

### Post by princeofnam on 2010-08-14
i tried googling about that, but I didn't come up with any concrete answers.

i'd also like to know people's opinions about taking out the windows master drive while installing ubuntu on the slave drive as i'm not entirely sure about the reasoning -- something to do with a GRUB confliction.

---

### Post by colin.p on 2010-08-14
I don't think you would notice any appreciable slow down. I ran 10.04 from an external 500GB USB drive, for a time, and frankly didn't notice any slow down. When I was satisfied that everything worked, to my satisfaction, I re-installed to the internal drive and it seems to be about the same speed.
Now granted, I did no proper speed tests or "blind testing" but it seemed to be the same.
If your bios allows you to choose which internal drive to boot from, you can disable the windows drive while you  install ubuntu to the second drive, and install grub to the second drive as well. When you boot, choose which drive to boot to. There is a boat load of threads to tell you how to do it, as well as any screw ups you may run into and how to fix them.

---

### Post by Ginsu543 on 2010-08-15
No, you shouldn't experience any slow-downs since Ubuntu doesn't care which partition it is installed in. In fact, you could install three different flavors of Ubuntu (let's say Lucid, Karmic, and Jaunty) all on different partitions on the same drive, or on different partitions on different drives, and each wouldn't care where it is or whether there are other releases installed as well.

As far as removing the Windows drive before you install Ubuntu, it's just a precaution so that you don't accidentally overwrite the Windows bootloader (NTLDR) with the bootloader Ubuntu uses, namely GRUB2. If you know what you're doing, this is not much of an issue, but removing the Windows drive will ensure that you don't mess up the NTLDR (which, in case you do, will prevent you from booting into Windows from that drive).

---

### Post by cascade9 on 2010-08-15
An ATA/IDE drive, running as 'slave' on any modern system will run just as fast as it would in 'master'.

---

