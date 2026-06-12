---
title: "kernel 2.6.35-25 broken graphics"
date: 2011-01-18
forum: General Help
---

### Post by pdkta on 2011-01-18
Hi guys!!! I have recently updated my ubuntu kernel to version 2.6.35-25 and its seems that broke my graphics. On login i cant see anything but some messy graphics. tryed to login with the old kernel and everything seems to work fine and also it works ok with the fglrx. The conflict seems to be beween the ATI open source drivers and the new kernel!!!

HP dv7  64 bit ubuntu 
radeon hd 4650

Please Help!!!

---

### Post by sacredfaith on 2011-01-18
Hey pdkta, 

Something similar happened to me and I think I did this:
[http://ubuntuforums.org/showthread.php?t=706163](http://ubuntuforums.org/showthread.php?t=706163)

If you weren't using Compiz, and were just using fglrx...this might help:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

However, I would wait for someone else (I'm still relatively new with graphics settings) to confirm these ideas!! 

Most Sincerely,

-sf

---

### Post by NotMarkus on 2011-01-18
I'm in the same boat.

This is what I see now, after the last update. :\

[IMG]http://imgur.com/th2mg.jpg[/IMG]

---

### Post by NotMarkus on 2011-01-18
Realizing that it was a kernel issue was a big help (I thought it was updated drivers that caused the problem). Anyway, I'm back up and running now. Thanks for making this thread pdkta. I figure I'll document what I did in case it can help anyone else.

I reverted to an old kernel. In order to do so, I had to edit the GRUB configuration so that I'd see the list of available kernels at boot.

Edit the file:

```
/etc/default/grub
```

Comment out this line:

```
GRUB_HIDDEN_TIMEOUT=0
```

More info: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Now run

```
sudo update-grub
```

in order to update the GRUB configuration file.

On boot, you should probably see a list of available kernels. I booted into 2.6.35-24 and it seems to be working perfectly.

---

### Post by efflandt on 2011-01-18
Did you use drivers from System > Administration > Additional Drivers or Synaptic (ie, Ubuntu packages), or did you download and manually install drivers directly from AMD?  In the latter case Ubuntu knows nothing about them, so modules for them will not automatically be added for the new kernel, and the drivers may need to be reinstalled.

There are x-swat ppa's if you need newer Ubuntu video driver packages than are normal for your Ubuntu version, for example [http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=maverick](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=maverick)

---

### Post by pdkta on 2011-01-19
Thanks for your support everybody!!!!
Like I said in my first post the problem doest occur with ATI proprietary drivers only with the open source drivers.

---

### Post by pdkta on 2011-01-25
moved to natty!!! :-)

---

