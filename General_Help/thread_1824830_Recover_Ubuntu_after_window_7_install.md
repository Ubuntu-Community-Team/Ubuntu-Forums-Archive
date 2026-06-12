---
title: "Recover Ubuntu after window 7 install"
date: 2011-08-14
forum: General Help
---

### Post by hemalchevli on 2011-08-14
I installed ubuntu inside windows, thing were going good, till windows got affected with virus, so had to reinstall it, now boots directly in windows 7.
I have a 500 GB HDD with two equal partions,
C: drive has windows
D: drive has ubuntu
I tried the boot-repair, didn't work, instead it corrupted windows boot, which got fixed using startup recovery
BUT 
I want ubuntu back...

---

### Post by mendhak on 2011-08-14
Hi, have you gone through the [help page]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") on this topic?  Assuming your Windows reinstall didn't use up the entire disk, Ubuntu should still be there and you can use the steps given on the page to recover it.

---

### Post by Duncan Williams on 2011-08-14
try `supergrub 2'
its a small program that you burn to a cd.
then boot your sys with the cd and it should give you access to ubuntu and windows.
if that works, it should also restore your grub.

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by Mark Phelps on 2011-08-14
> **Duncan Williams said:**
> try `supergrub 2'
its a small program that you burn to a cd.
then boot your sys with the cd and it should give you access to ubuntu and windows.
if that works, it should also restore your grub.

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

OP said clearly "inside windows" ... meaning, this is a Wubi installation.  Wubi does NOT use GRUB -- so installing it is only going to make things worse.

To the OP: When you reinstalled Win7, you wiped out the registry entries for Wubi.  It was installed like any other app.

What you can try, and has sometimes worked, is to save off the root.disk file on your "D" drive to an external drive, reinstall Wubi to the same drive, and then copy back your old root.disk file.

---

### Post by hemalchevli on 2011-08-14
> **Mark Phelps said:**
> OP said clearly "inside windows" ... meaning, this is a Wubi installation.  Wubi does NOT use GRUB -- so installing it is only going to make things worse.

To the OP: When you reinstalled Win7, you wiped out the registry entries for Wubi.  It was installed like any other app.

What you can try, and has sometimes worked, is to save off the root.disk file on your "D" drive to an external drive, reinstall Wubi to the same drive, and then copy back your old root.disk file.

yes it was wubi install, i'll do what you said
Thanks
will post if its a success..

---

### Post by Duncan Williams on 2011-08-14
Kewl, I have never used wubi, but had similar problem with dual-boot. Jumped the gun a bit.. Learnt today that wubi has no grub..  As far as I no, supergrub boots you into and repairs grub, it shouldn't create one.

---

### Post by Mark Phelps on 2011-08-14
> **Duncan Williams said:**
> Kewl, I have never used wubi, but had similar problem with dual-boot. Jumped the gun a bit.. Learnt today that wubi has no grub..  As far as I no, supergrub boots you into and repairs grub, it shouldn't create one.

While that is true ... if they are careless and DO force GRUB to install -- they run the risk of hosing up their Win7 boot and rendering it unbootable.

So, BEFORE you blindly tell folks to install GRUB, make sure they are NOT using a Wubi install in the future, OK?

---

### Post by Duncan Williams on 2011-08-15
look, I am not getting into pedantics.
Other than `inside' it sounded to me like a dual boot.

I never said to install grub, I said to use supergrub to boot into his grub to access ubuntu.

Fair enough as I said `I jumped the gun'

If you only knew how much bad advise is given in the myriad of self-help forums that I have visited.

My suggestion was an attempt to help the OP.

end of story, peace out.

---

### Post by hemalchevli on 2011-08-15
While installing ubuntu via wubi again, it hanged, so i just decided to let go,
removed the ubuntu files from D: drive and installed ubuntu on a new partition.


mendhak, Duncan, Mark, Thank you

P.S. : This was my first thread, I'll try to be more clear of the problem next time.

---

