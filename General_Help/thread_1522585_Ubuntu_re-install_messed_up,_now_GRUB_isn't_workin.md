---
title: "Ubuntu re-install messed up, now GRUB isn't working"
date: 2010-07-02
forum: General Help
---

### Post by brizzenden on 2010-07-02
So I've only been using ubuntu for a few months now, so I'm still pretty fresh to all of this. And over the last couple months I've been messing with settings, and last night I ended up doing something with my sound and I lost all sound on my laptop. 

I looked around online for a way to fix it, but seeing as I just turned my laptop on and there was no sound, I'm not sure what I did, and therefore I wasn't sure how to fix it.

I figured that since I had nothing of value stored on my laptop, reinstalling ubuntu wouldn't hurt.

I was running 10.04 but all I had was a 9.04 disc.  So I put it in and get half-way through, when it suddenly freezes on the install.  I gave it a while thinking it would start up again and it didn't.  So I turn off my laptop and turn it on.  Only this time it goes to a black screen and says:

error: file not found.
grub rescue>

I reset the computer a few times and finally the liveCD worked again and I went back to install, but this time it skipped the install and went to the live desktop.

I read on similar posts about some commands, and I tried all of them, but nothing worked.  I figure since I had 10.04 installed before I messed this whole thing up, my system probably has GRUB 2.  Where as 9.04 comes set up with GRUB.  Could this be the problem and I just need to install 10.04 from a disc?  Please tell me I haven't royally f***** up my laptop.

---

### Post by clrg on 2010-07-02
You have not royally spanked your laptop. Probably the installation of 9.04 crashed before it could install GRUB, and now you have an incomplete installation of 9.04.

I recommend you to download 10.04 (since you are able to write this I assume you have access to another computer), burn it to disc, and reinstall properly.

If you want to repair GRUB, I recommend the Super GRUB Disk ([http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)), but since your laptop froze during the installation, the system may not even be able to boot, therefore rendering any repair attempts useless.

---

### Post by brizzenden on 2010-07-02
> **clrg said:**
> If you want to repair GRUB, I recommend the Super GRUB Disk ([http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)), but since your laptop froze during the installation, the system may not even be able to boot, therefore rendering any repair attempts useless.

Are you meaning any attempts to repair GRUB are likely useless?

Because if so I don't care whether I have GRUB or GRUB 2.

---

### Post by clrg on 2010-07-02
That's exactly what I am saying. You will be able to repair GRUB, but that won't help you, since the installation process failed. Your system will most likely not boot.

---

### Post by spydeyrch on 2010-07-02
Yeah, your best bet is to get access to a copy of 10.04. Use that to format your HDD and reinstall. It will reinstall grub2. 

Also, if possible, make a live usb instead of a live cd. It will load faster and install faster. Plus then you can take it with you where ever you go and have access to a copy of ubuntu when ever needed. Very handy to have. I have used my customized one on many ocassions to repair my family & friends computer, and all I needed was a little USB flash drive (thumb drive).

If you would like help making a live usb, let me know and I will do what I can to help. ;)

-Spydey

---

### Post by gbttun on 2010-07-02
Hi,

I'm wondering if the SGD will work for my problem as well. I have an Ubuntu/openSUSE laptop; yesterday, I was trying out a new distro by USB. After restarting, my computer has reverted to an older version of GRUB (whatever GRUB comes with openSUSE), not the GRUB 2 I'm used to seeing. The SUSE GRUB only shows my SUSE partition. When I booted an Ubuntu LiveCD, however, my Lucid Lynx filesystem is still on my hard drive somewhere.
Will using the SGD restore GRUB2?

Thanks in advance.

---

### Post by spydeyrch on 2010-07-02
> **gbttun said:**
> Hi,

I'm wondering if the SGD will work for my problem as well. I have an Ubuntu/openSUSE laptop; yesterday, I was trying out a new distro by USB. After restarting, my computer has reverted to an older version of GRUB (whatever GRUB comes with openSUSE), not the GRUB 2 I'm used to seeing. The SUSE GRUB only shows my SUSE partition. When I booted an Ubuntu LiveCD, however, my Lucid Lynx filesystem is still on my hard drive somewhere.
Will using the SGD restore GRUB2?

Thanks in advance.

So, I am not exactly sure if the SGD will work, as I have never used it. But if you want a somewhat simple work-around. You could always just update your opensuse grub to include your ubuntu install. Then when you boot, your opensuse grub will come up and show both opensuse, ubuntu, and any other installs.

I haven't used opensuse since around 2007, maybe it was 2006, so I am not exactly sure if opensuse truly does use grub as it's bootloader.

But, what I can say, is that if it does use grub as its boot loader, even if it is grub and not grub2, you can update it and it will include ubuntu in the boot list. I have win7, mint8 (now mint 9), and ubuntu 10.04 installed. I updated mint 8's grub and it found ubuntu just fine, no issues.

I am also not sure what the cli command would be in opensuse. I know that it uses  "su" instead of "sudo" and I don't remember what the other commands would be to update grub.

Anyone else?

Hope that helps. :D

-Spydey

---

### Post by brizzenden on 2010-07-06
Sorry it's a few days late, but I did get it to work.  I used DBAN to nuke the hard drive because the 10.04 install froze just like the 9.04 install, at the exact same place.  

Anyway, after nuking the HD, 10.04 installed perfectly and everything is working pretty normally.  There's a few little problems but I think it's just a matter of downloading the same plugins I had before.

Thanks to everyone who helped.

---

