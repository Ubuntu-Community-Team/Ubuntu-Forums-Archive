---
title: "Grub_xputs not found: no working cd-rom and USB. HELP!!"
date: 2011-01-07
forum: General Help
---

### Post by Singe2020 on 2011-01-07
When trying to salvage my faulty main desktop computer I used Ubuntu to solve several of my problems. My windows partitions didn't recognize my USB root hubs anymore, and I couldn't boot my install cd's.
 
After I installed Ubuntu it seemed all peachy, but after a short while my problems resurfaced. I managed to fiddle around with my hardware and I learned not a thing. The problems kept on coming back. :confused:
 
Then I reconfigured my system, and for a few hours it worked again. I burned a Ubuntu live CD with the intention of booting from it. That failed. I managed to update Ubuntu 10.04 to Ubuntu 10.10 through update manager, it mentioned an error in the grub unknown to me so I continued. On rebooting I got the terror message grub_xputs.
 
I managed to learn that no terminal command works what so ever in grub rescue. I can't boot from a live CD. I cant boot from USB port neither.
 
The only commands grub rescue responds to are:
ls
prefix=
root=
 
Does anyone know how to revitalize grub **from within grub rescue?**
 
Thank you all for your time.
 
Greets Singe

---

### Post by drs305 on 2011-01-07
Singe2020,

Welcome to the Ubuntu forums and sorry for the problem that brought you here.

The xputs message normally means that parts of Grub2 are not fully installed. That means you probably aren't going to get it to work. The installation/LiveCD is usually a system-saver from which you can restore your boot files. 

Since you can't use the LiveCD, you can give the following a try with your existing Grub2. There is a possibility you can get it to boot depending on which parts of the Grub2 files are corrupted. It's not a high chance, but it's something.
[Grub Rescue Prompt Megathread ]("http://http://ubuntuforums.org/showthread.php?t=1594052")

If you have a copy of the ISO on a partition you can find from the grub prompt, you may be able to get the ISO to boot without a CD. Here is the link to that thread:
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

Best of luck.

---

### Post by Singe2020 on 2011-01-07
Thanks for the responce drs305. I'll try my hand at the solutions you suggested, after I get some much needed sleep. 
- . -
 
zzz

---

### Post by Singe2020 on 2011-01-09
Aha, this is seeming to become a problem of a missing grub.cfg file.
 
Through browsing with the ls option I can't find it in the usual locations, not in '/boot/grub', 'lost+found', 'bin' or 'usr/lib/grub/i386-pc'. 
 
The insert module (insmod) command gives an unknown file prompt.
 
I guess I need to reinstall the grub by hooking the harddrive to a friends computer and booting a live CD there.
 
Is there a way to search the grub file with a command?

---

### Post by drs305 on 2011-01-09
> **Singe2020 said:**
>  
Is there a way to search the grub file with a command?
From a running OS one command to find it would be:
```
sudo find / -type f -name grub.cfg
```

If you were running from a LiveCD, you would have to mount your Ubuntu partition and then run:
```
sudo find /<mountpoint> -type f -name grub.cfg
```

However, finding the grub.cfg file probably isn't the end of your problems. If you can boot a LiveCD I'd suggest using the *chroot* procedure, linked in my signature line. There is a good chance that the problem is larger than just a missing grub.cfg file. The chroot procedure to purge/reinstall Grub2 will make sure all the boot files are correct.

---

