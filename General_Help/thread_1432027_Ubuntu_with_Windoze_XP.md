---
title: "Ubuntu with Windoze XP"
date: 2010-03-17
forum: General Help
---

### Post by disco.sleeze on 2010-03-17
Hi Guys,

My PC came with Windows Vista installed.  After getting fed up, I turned to Ubuntu.  I installed it on a separate partition and am dual-booting, because I still need to be able to use Windows for work.

My Vista installation has become very unstable (surprise, surprise), and I was wondering if it is possible to install Windows XP instead on that partition, without messing up my Ubuntu installation?

I hope this isn't more of a Windows help question!

Thanks!

---

### Post by perham on 2010-03-17
> **disco.sleeze said:**
> Hi Guys,

My PC came with Windows Vista installed.  After getting fed up, I turned to Ubuntu.  I installed it on a separate partition and am dual-booting, because I still need to be able to use Windows for work.

My Vista installation has become very unstable (surprise, surprise), and I was wondering if it is possible to install Windows XP instead on that partition, without messing up my Ubuntu installation?

I hope this isn't more of a Windows help question!

Thanks!

install windows and then follow here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jtprince on 2010-03-17
This can be done (I've done similar things many times).  You will likely run into two issues:
1.  XP may not "happily" install over Vista.  If it won't install over your Vista partition, you can get around this by wiping clean your vista partition (be careful you get the right partition) using gparted or even the liveCD.  Once clean, you should be able to easily install XP on that partition.
2.  After an XP install, you will have probably wiped out your grub boot loader.  You can fix this with the liveCD (see [here]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/") or similar).

Good luck!

---

### Post by bpalone on 2010-03-17
Short answer --- Yes.


I haven't done it, so hopefully someone that has will chime in here to fill in the blanks.  First thing is to back up any data you value from both OSes, an ounce of prevention is worth a whole bunch if things go bad.  hey shouldn't go bad, but it better to be safe than sorry.

I would probably get and use GParted Live and just whack the Vista partition.  Then, I would create a new partition in its place for XP and go ahead and format it to NTFS.  Then just do a normal Windows XP install, but be sure to tell it to use the partition you just created.  In this process it will whack the MBR and Grub.  With the old version of Grub it is easy to fix, but I am unsure about how it is with the new Grub.

Hopefully, someone who has done it will pipe in.  You could also try searching for installing XP after Ubuntu install.

Good luck.

---

### Post by disco.sleeze on 2010-03-17
Thanks for all of the input guys.  This sounds scarier than I was hoping...lol.

I'll give it a go when I'm feeling brave.

---

### Post by linden940 on 2010-03-17
hmmm i have never tryed this but if you put the disk in there and go 2 install it as if u did NOT have anything ON there but one OS you will come to a partion screen...just make sure you use the partion that was for the windows...

---

