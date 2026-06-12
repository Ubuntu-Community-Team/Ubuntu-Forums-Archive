---
title: "GRUB loading error: no such partition (Again)"
date: 2011-12-10
forum: General Help
---

### Post by steve48 on 2011-12-10
Hi everybody,
I've spent several hours trying to find a solution but haven't found any yet.
I have a netbook so no CD/DVD drive.
I had windows 7 installed and I installed linux !
Then I decided to delete linux by deleting the partitions. Big big mistake.

Now when I boot I have "no such a partition".

The good news is that I have parted magic in an usb key which gives me access to all the partitions and the files.
I have 2 partitions :
one for windows and one system reserved (2 folders boot and system information), however I tried to modify those 2 folders but there's no change in the boot.
I tried to change the flag of each partition into "boot" but still doesn't work.

I conclude that the problem is coming from the windows partition, there's certainly a file to modify, what do you think ?

---

### Post by Rubi1200 on 2011-12-10
Hi and welcome to the forums :-)

From the live USB, post the results of the boot info script (link at the bottom of my post with instructions).

Thanks.

---

### Post by coffeecat on 2011-12-10
> **steve48 said:**
> 
I conclude that the problem is coming from the windows partition, there's certainly a file to modify, what do you think ?

No. My guess is that the problem is in the mbr. You have grub code there which is looking for the Ubuntu root partition which has the grub menu and some essential grub code. Without it, it errors out.

So - do you have Windows only on that machine now, and want to boot into Windows only? (You would need to re-install the Window mbr.)

Or:

Do you want an Ubuntu/Windows dual-boot?

If you answer that, we can tell you how to proceed.

By the way, I suggest you do not use partition magic until we've clarified the above, if at all.

**EDIT**: and what Rubi1200 says. I agree. :)

---

### Post by steve48 on 2011-12-10
thank you guys for your quick reply.
I only want windows now...
If it can help I have a reinstall windows partition but there's no option to repair. I really really want to avoid to reinstall the whole windows. ;)

---

### Post by coffeecat on 2011-12-10
The recovery partition won't help, unfortunately. You need "bootrec.exe /FixMbr" from a Windows command prompt. But that's fiddly when you don't have a CD drive. Easiest thing is to use an Ubuntu live USB. Have a look here:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

Those are three alternatives to installing the Windows mbr. Boot up with an Ubuntu live USB, make sure you are connected to the internet so that you can download the package(s) needed and try the lilo method. It's not identical to the Windows mbr, but it installs functionally identical code. So long as your Windows boot partition has the boot flag set, Windows will then boot.

You probably need to do a:

```
sudo apt-get update
```

... before running the commands in that link.

If that doesn't work, then we do really need the output of the boot script as Rubi1200 advised.

---

### Post by steve48 on 2011-12-10
thank you, i'll have a look. :D

---

