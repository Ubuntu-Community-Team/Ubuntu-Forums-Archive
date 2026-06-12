---
title: "Asus G50VT Enhanced vs Compatible: GRUB"
date: 2009-09-28
forum: General Help
---

### Post by Xorlium on 2009-09-28
Hi,

I have an Asus G50VT laptop with two hard drives. The first of them contains windows vista 64, and the second one used to have ubuntu 9.04. I used to load with grub and everything was fine. Well, not everything.

You see, the thing with this specific laptop is that linux doesn't like the default BIOS configuration and it doesn't work well unless I set the setting "Advanced-> IDE Configurtion->Sata Operation Mode [Compatible]" (as opposed to "Advanced-> IDE Configurtion->Sata Operation Mode [Enhanced]", which is what windows needs).

Now, I used to make it work by just switching between Enhanced and Compatible when I wanted to boot to windows.

I started experiencing hard drive problems. I had to re-install ubuntu a couple of times. It works for a little while, and then after 4 or 5 boots it always checks the disk because of errors, then it works. Then the next time it just fails. and I have to run fsck manually and then it has to fix many inodes and whatnots. Then it fails.

So the hard drive is probably failing. But that isn't the point. I think it's a hard-drive problem, because at boot, if I now set it to "Enhanced", the BIOS doesn't even detect the second hard drive (it used to). If I set it to compatible and reboot, then it does detect the hard drive and grub loads fine.

But of course, this means I can't get into vista, because if I set it to enhanced, the BIOS doesn't detect my second hard drive, and so grub says: Error 21.

If I set it to compatible, I can't load vista (it just doesn't work), but I can load ubuntu. But ubuntu will fail for the n-th time, I'm sure, in a couple of boots.

Now, I know you guys won't have an answer to this. But I'm not an expert, so I don't even know where to look for an answer. Where do I start? I'm not even sure it's a problem with the hard drive. Because when I re-install ubuntu, it works fine the first few boots. And since money is kind of tight, I'd like to make sure before I go buying a new one. Is there something I can do? Like a test or something?

Or is there a way to install GRUB from the LiveCD in a way that recognizes windows?

Thanks

---

### Post by Xorlium on 2009-10-03
bump

Xorlium

---

### Post by digz6666 on 2009-10-24
My ASUS N50VN also has same problems.

My hard drive sometimes not recognizes on enhanced mode 2 days ago.
It was normal for 7 months from buy time.
So I'm thinking of buying new hard disk. Maybe the sata port has error. So I'll buy new hard disk and test.

But when I plug my hard into usb port and boot it's fine.
Too weird.

Anyone has same problems?
Any suggestions?

---

