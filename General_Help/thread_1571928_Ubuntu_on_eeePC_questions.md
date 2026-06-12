---
title: "Ubuntu on eeePC questions"
date: 2010-09-10
forum: General Help
---

### Post by Rypervenche on 2010-09-10
I am planning on buying a new laptop, but since money is tight I will probably be getting a netbook/eeePC. I have seen that some hardware problems exist for certain eeePCs and I was wondering what problems will/might I incur when running Ubuntu on it? I know there is Aurora (previously Eeebuntu) but since I already know Ubuntu and its compatibility, I would prefer to stay with that. Does Ubuntu work well on eeePCs and other netbooks?


Also, since I will be using this netbook for my main computer I plan on doing pretty much everything I normally do on my normal computer on it. That being said, for using Windows I don't want to partition the already small HDD. Will it be possible to VM Windows? I'm very new to the concept of VMing, but is that a choice I have?

Thanks in advance^^

---

### Post by hrickh on 2010-09-10
> **Rypervenche said:**
> 
Also, since I will be using this netbook for my main computer I plan on doing pretty much everything I normally do on my normal computer on it. That being said, for using Windows I don't want to partition the already small HDD. Will it be possible to VM Windows? I'm very new to the concept of VMing, but is that a choice I have?

I have a lowly 701 4G that I run Ubuntu 10.04 on no problems.  I also run Virtualbox with an XP instance from an SD card (very rarely these days).  It's not fast, but it works. It takes a good while to get XP up and running, but once it's running things are fine.

R.
==

---

### Post by snowpine on 2010-09-10
Ubuntu is one of the very best distros for netbooks!

You may find this list helpful:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

As far as virtualizing Windows, I would not recommend it on a netbook. The hardware is just not powerful enough for a VM to be as fast as a dual boot.

A dual boot will be faster, and will occupy the same amount of hard drive space anyway. (Windows does not magically become smaller if you install it in a VM!)

If you want to use both Ubuntu and Windows at the same time using a VM, I would recommend saving up for a proper laptop with a faster processor and lots of RAM.

---

### Post by hsoulen on 2010-09-10
I run a 1201n with Lucid and it rocks!

Only issues I ran into were with wireless but Realtek has a solid kernel 2.6 driver which is updated regularly.

As for VMs, VirtualBox does work and I have a couple (Win2K3 and a Windows 7) but remember that the Atom processor does not support VT (hardware virtualization) so things will run a bit slow, remember to up your RAM no matter what. 1GB is a minimum, any "buntu" will run with less but you won't be happy.

Good luck and post your results if you get one!

Hank

---

### Post by Rypervenche on 2010-09-10
> **snowpine said:**
> As far as virtualizing Windows, I would not recommend it on a netbook. The hardware is just not powerful enough for a VM to be as fast as a dual boot.

A dual boot will be faster, and will occupy the same amount of hard drive space anyway. (Windows does not magically become smaller if you install it in a VM!)

If you want to use both Ubuntu and Windows at the same time using a VM, I would recommend saving up for a proper laptop with a faster processor and lots of RAM.
Thanks for the advice, but I still think that I would prefer VMing. I would like to devote all of my HDD to Linux without partitioning it. I realize that it will be slower, but I have no problems with speed. As long as it works, then I am happy. RAM may be a problem, so I'll have to look into that.

Thank you everyone for the answers. It looks as though I'll be buying a new netbook sooner than I had expected. :)

---

### Post by Rypervenche on 2010-09-10
Actually, that should have been in question form. Since speed isn't an issue for me, will Windows XP still run under a VM on a netbook?

---

### Post by snowpine on 2010-09-10
> **Rypervenche said:**
> Actually, that should have been in question form. Since speed isn't an issue for me, will Windows XP still run under a VM on a netbook?

The answer likely depends on what you use Windows for. :) What are your needs?

It certainly won't work for gaming, multimedia, or anything that relies on specific hardware. It should work OK for surfing the web, word processing, etc... but you can do all those things in Ubuntu too. ;)

---

### Post by Tom Collier on 2010-09-10
I run dual-boot Karmic (full boat Karmic, not the netbook remix) and XP on an eee1000HD, with a third drive for data and file storage that both operating systems share. I only use the Windows side for one specific application and occasionally to print to a Lexmark wifi printer that doesn't have any Linux drivers available.

I do nearly everything else on the Ubuntu side, including maintain a 6,000 name mailing list, graphics stuff using both GIMP and Inkscape, and oh by the way, video editing using OpenShot. Just recently started using a 16GB SD chip for data/file storage.

This netbook is my only computer and I've never found it to be underpowered or overwhelmed by anything. I'm not the type who frets over CPU clock speed or other geeky stuff like that. I just need to get work done and this setup does it quickly, efficiently, and well. I am not a gamer and deleted everything but Blackjack on my netbook. (Vegas isn't that far away from where I am, heh!)

I had one initial problem with wifi but that turned out to be a router problem, not anything to do with the eeepc netbook. Eventually, I'll upgrade to the latest LTS, but for now, I'm happy with both the hardware and software.

---

### Post by hrickh on 2010-09-10
> **snowpine said:**
> The answer likely depends on what you use Windows for. :) What are your needs?

It certainly won't work for gaming, multimedia, or anything that relies on specific hardware. It should work OK for surfing the web, word processing, etc... but you can do all those things in Ubuntu too. ;)
True.

The only reason I keep a Win VM around is for the increasingly rare times I get a request from an agency for a file in a very specific format that just can't be created outside of Windows (Trados files, in my case).

R.
==

---

