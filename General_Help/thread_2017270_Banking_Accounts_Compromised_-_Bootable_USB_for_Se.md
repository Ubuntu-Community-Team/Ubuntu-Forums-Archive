---
title: "Banking Accounts Compromised - Bootable USB for Security?"
date: 2012-07-05
forum: General Help
---

### Post by Guysakar on 2012-07-05
Hello guys and gals.

After having some accounts compromised, I am trying to figure out a safer way to do banking online. My idea is to have a separate operating system which is used solely for sensitive computing.

I have an XPS 13 with Windows 7 Home Premium with a 128 G SSD, so space is a bit of a concern.

My idea was to make a Windows 7 bootable USB, but it is appearing very difficult and someone said it takes about 20 minutes to boot. That's too long.

So now I am thinking of maybe Linux or Ubuntu or something. Does this sound like the best course of action to accomplish my goal of having a virus free OS that is used only for logging into my online banks?

Also, could I install Linux or Ubuntu on my actual hard drive and just choose to boot from that vs. my standard Windows 7? Would I have to completely reformat and partition the HDD to accomplish this? Also, if I did it this way, and I had a virus on my Windows 7, would that leak over to the Linux or Ubunutu when running from there?

Side not, I have never used either Linux or Ubuntu, so any suggestions will be greatly appreciated.

Thank you.


PS How long does it usually take to boot Ubunutu from a UDB?

---

### Post by raja.genupula on 2012-07-05
I suggest you to use a separate browser and that too in private mode of browsing .A separate browser and only for bank logins .

---

### Post by vasa1 on 2012-07-05
I never had any problems banking online, trading online, transferring money online  or paying bills online even when using MS Windows. And I use my regular browser.

---

### Post by sudodus on 2012-07-05
Welcome to the Ubuntu Forums :-)

> **Guysakar said:**
> Hello guys and gals.

After having some accounts compromised, I am trying to figure out a safer way to do banking online. My idea is to have a separate operating system which is used solely for sensitive computing.

I have an XPS 13 with Windows 7 Home Premium with a 128 G SSD, so space is a bit of a concern.

My idea was to make a Windows 7 bootable USB, but it is appearing very difficult and someone said it takes about 20 minutes to boot. That's too long.

So now I am [COLOR="Red"]thinking of maybe Linux or Ubuntu or something[/COLOR]. Does this sound like the best course of action to accomplish my goal of having a virus free OS that is used only for logging into my online banks?

It is a good idea. I would suggest Lubuntu which is Ubuntu with the ultra-light-weight desktop environment LXDE.

You can use

1. a regular CD or USB bootable drive and run a live session without any further installation.

2. a persistent USB live system (add a casper-rw file or partition to a USB system '1. + casper-rw'). This can be updated and upgraded except the linux kernel.

3. install a system to USB drive like you would install a system to an internal hard disk or solid state drive. This can be completely updated and upgraded.
> 
Also, could I install Linux or Ubuntu on my actual hard drive and just choose to boot from that vs. my standard Windows 7?

Yes, either the 'full install' as dual boot, or a 'wubi' install, or a virtual machine (for example Oracle VirtualBox) with Ubuntu installed inside the virtual machine.
> 
Would I have to completely reformat and partition the HDD to accomplish this?

Only with the 'full install'. If you use Lubuntu without extra bells and whistles, and don't save a lot of private files, it would need only 4 GB, but I would recommend at least 8 GB if possible.
> 
Also, if I did it this way, and I had a virus on my Windows 7, would that leak over to the Linux or Ubunutu when running from there?

I would say no, because Windows cannot read the linux file systems (ext3 or ext4).
> 
Side not, I have never used either Linux or Ubuntu, so any suggestions will be greatly appreciated.

Thank you.


PS How long does it usually take to boot Ubunutu from a UDB?
Maybe a few minutes depending of which system you choose. Anyway much less than 20 minutes. A drive of type 1. (a regular CD or USB bootable drive and run a live session without any further installation) is the fastest (but without updates), so if you want security updates, use something else. A drive of type 3. (install a system to USB drive like you would install a system to an internal hard disk or solid state drive) would be the slowest partly due to the fact that USB is slow reading many small files compared to few big files (with the same amount of data).

You should choose a higher-grade USB flash drive with documented high read and write speed. For example, choose a USB 3 drive (even though you cannot boot from a USB 3 port, the flash system inside it is faster, and that is usually limiting the data transfer rather than the USB interface).

Finally have a look at this link [[COLOR="red"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by Grenage on 2012-07-05
> **Guysakar said:**
> PS How long does it usually take to boot Ubunutu from a USB?

If you're using a 'live' image, it will probably take well under a minute.  If you're using an 'installed' USB, it can take a liitle longer, but generally not much.

I'm a big fan of USB installs; they're so portable and convenient.

---

### Post by chocklet on 2012-07-05
For maximum security put Linux on an SD card (sudodus' option #1, no persistence) and write protect the card.  You won't be able to save configuration, but if your only activity is banking and perhaps web-based email, you should be fine. (but if you open email before banking, be careful about what email attachments you open!)   You will probably need a USB card reader as many notebooks don't boot from their internal card reader.

After you finish banking and email activity, then you can visit any sites you wish, because any malware you might pick up will be lost when you reboot.  You can export and import bookmarks to your hard drive or other storage device.

Ubuntu Unity may be perfect for you. Or...

If you want the latest kernel and newer drivers, Knoppix 7.0.3 was just released.  Knoppix (DVD version) includes several browsers (IceWeasel is Firefox), printer drivers and LibreOffice.  The DVD version requires an 8GB SD card.

If you don't have a hardware firewall (included on some routers), the  first thing to do after booting is start the firewall.  It seems a bit  paranoid, but I see that I'm constantly being pinged by unknown parties  from all over the world so I'd go with a firewall.  On Knoppix it's just 3 clicks.

---

### Post by Quatrix on 2012-07-05
A separate OS is major overkill.  Could you explain a little about how your accounts were compromised in the first place?

---

### Post by msammels on 2012-07-05
> **Quatrix said:**
> A separate OS is major overkill.  Could you explain a little about how your accounts were compromised in the first place?

I'm not too sure it is. I mean, you can harden Linux, probably more than you can harden Windows, since it is designed for servers as well as desktops. I mean, if he really wants to be secure, this could be the way to go.

---

### Post by kurt18947 on 2012-07-05
> **Grenage said:**
> If you're using a 'live' image, it will probably take well under a minute.  If you're using an 'installed' USB, it can take a liitle longer, but generally not much.

I'm a big fan of USB installs; they're so portable and convenient.

+1 on a 'real' install.  I used Gparted on a 'generic' 8 gig USB drive (Centon).  Deleted the partition, recreated an ext2 partition with the boot flag set (no swap - I understand flash swap partitions are not great ideas.)  I then installed Xubuntu from a CD.  The install went fairly quickly, about 30-45 minutes.  Updates were another story.  For whatever reason, updates took 2+ hours.  An advantage to 'real' installs is the ability to install security and other updates.  AFAIK live USB installs cannot accept updates.  My USB install will boot in around 3 minutes.  Ubuntu from the hard drive takes around 40 seconds so not too bad.  No java anything (so far anyway), no flash.  I plan to use that drive ONLY for secure transactions on reputable web sites.  Durability?  I just did this and don't plan on using it much so time will tell, I guess.

---

### Post by Habitual on 2012-07-05
> **Quatrix said:**
> A separate OS is major overkill...

certainly is overkill.
I too like vasa1, "have never had any problems banking online, trading online, transferring money online or paying bills online" but ***in Linux***.

---

### Post by sudodus on 2012-07-05
> **kurt18947 said:**
> For whatever reason, updates took 2+ hours.  An advantage to 'real' installs is the ability to install security and other updates.  AFAIK live USB installs cannot accept updates.

My experience of file transfer to USB drives makes me think that it is slow due to the fact that USB is slow reading many small files compared to few big files (with the same amount of data).

Persistent USB installs can update and install programs, but it cannot update the kernel.

Anyway, I have solved the problem of very slow updating by cloning the USB drive to the internal hard drive of an old laptop, where I update it fast. Including cloning back and forth it is still much faster and I guess it also saves the USB drive from excessive wear.

---

### Post by sammiev on 2012-07-05
I do online banking and so on with my current OS which is Linux. I start my computer and use Private Browsing. I go online, sign in do my stuff and sign out and do a fresh reboot before doing anything else. I never had problems from day one. :)

---

### Post by kurt18947 on 2012-07-06
> **sudodus said:**
> My experience of file transfer to USB drives makes me think that it is slow due to the fact that USB is slow reading many small files compared to few big files (with the same amount of data).

Persistent USB installs can update and install programs, but it cannot update the kernel.

Anyway, I have solved the problem of very slow updating by cloning the USB drive to the internal hard drive of an old laptop, where I update it fast. Including cloning back and forth it is still much faster and I guess it also saves the USB drive from excessive wear.

I suspect a separate partition/OS on a hard drive is the best solution.  A flash drive is nicely portable though.   I'm not sure how much of a factor flash RAM wear would be on a USB drive used for say, less than 1 hour/month.

---

