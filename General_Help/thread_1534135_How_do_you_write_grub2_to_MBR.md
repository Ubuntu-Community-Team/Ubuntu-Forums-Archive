---
title: "How do you write grub2 to MBR?"
date: 2010-07-19
forum: General Help
---

### Post by LanceHaverkamp on 2010-07-19
I have made a new /boot/grub/grub.conf file.  

How do I write it to MBR?  Do I have to be running from CD?

I can't find new Grub2 instructions anywhere.

Thanks,
Lance

---

### Post by Kay The Bantu on 2010-07-19
I found this tutorial, seems pretty thorough. Hope it helps ;)

[http://www.dedoimedo.com/computers/grub-2.html]("http://www.dedoimedo.com/computers/grub-2.html")

---

### Post by Blackbird_13 on 2010-07-19
Did you install grub2 from a fresh install of lucid? If so, the standard install should have written a small amount of grub2 code to your MBR which will point to your /boot/grub/grub.cfg on boot.
My understanding is that whenever grub.cfg is updated you do not have to update the MBR.

If you use another boot loader, but now want to use grub2 I think this should work:

sudo grub-mkconfig -o /boot/grub/grub.cfg /dev/sda

WARNING be absolutely sure how your current boot loader is configured and that you really do have grub2 installed in /boot/grub/ before running the above command.

---

### Post by LanceHaverkamp on 2010-07-19
OK Thanks, I'm getting a little further:

```
sudu update-grub
```
or its exact same longer twin
```
sudo grub-mkconfig -o /boot/grub/grub.cfg 
```
compile the menu, but don't install it into MBR.
```
sudo grub-install /dev/sda
```
should send it to MBR, but I'm gettng the following error:

/usr/sbin/grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

which is really stupid because it worked fine when I installed kubuntu 10.04 into that partition in the first place.  It might be complaining because it's reiser, not ext3, but as I said, it figured this out when I installed 10.04, so a simple reinstall should not be a problem.

Any other ideas?

---

### Post by Blackbird_13 on 2010-07-19
Not experienced this.

This may help:

[http://ubuntuforums.org/showthread.php?t=1358123](http://ubuntuforums.org/showthread.php?t=1358123)

---

### Post by philinux on 2010-07-19
> **LanceHaverkamp said:**
> I have made a new /boot/grub/grub.conf file.  

**[COLOR="Blue"]How do I write it to MBR?[/COLOR]**  Do I have to be running from CD?

I can't find new Grub2 instructions anywhere.

Thanks,
Lance

You dont. Grub is installed to the mbr at installation and points at grub.cfg which is created from a bunch of scripts. The main one being /etc/default/grub. update-grub re-creates /boot/grub/grub.cfg

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by LanceHaverkamp on 2010-07-19
Ah, that would explain what I'm seeing.  Then how do I tell MBR to look for grub.conf on sda1 instead of where it's apparently looking now, on sda4?

---

### Post by philinux on 2010-07-19
> **LanceHaverkamp said:**
> Ah, that would explain what I'm seeing.  Then how do I tell MBR to look for grub.conf on sda1 instead of where it's apparently looking now, on sda4?


Run this script and post back the results.txt file as an attachment.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by LanceHaverkamp on 2010-07-19
I installed kubuntu on sda1, then I installed lubuntu on sda4.

sudo grub-install /dev/sda  is returning errors, as listed above. 


Results are attached.
Thank you for your assistance.

---

### Post by philinux on 2010-07-19
Boot info Summary from your results.txt file.

```
Grub 2 is installed in the MBR of /dev/sda and looks at sector 379507334 
    of the same hard drive for core.img, [B][COLOR="Red"]but core.img can not be found at this 
    location[/COLOR][/B].
```

Something must have gone wrong to cause this. I would re-install grub2 to /dev/sda from the livecd using a chroot. Or from the links I gave you provided previously. There is more than one way. ;)

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by LanceHaverkamp on 2010-07-19
Thanks!  [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html) solved it, but only when using the --force option which uses the block address rather than the partition location.

The new results say

```
 => Grub 2 is installed in the MBR of /dev/sda and looks at
sector 7359129 of the same hard drive for core.img, but core.img
can not be found at this location.
```

But it works!

Thanks again to all of you!

---

