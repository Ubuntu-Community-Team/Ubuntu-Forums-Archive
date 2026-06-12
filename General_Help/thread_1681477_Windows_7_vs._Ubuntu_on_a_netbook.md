---
title: "Windows 7 vs. Ubuntu on a netbook"
date: 2011-02-04
forum: General Help
---

### Post by ?#Yhf%*&amp; on 2011-02-04
I'm planning on getting a netbook soon (probably in May), and the model I want (Asus EEE PC 1001PX-EU17-BK) comes with Windows 7 Starter. Should I keep Windows 7, install Ubuntu 11.04, or dual-boot?

I have already found intructions on how to dual boot the way I want, and how to change the wallpaper in Windows 7 Starter. :p I also already have experiance with Ubuntu, Unity 3D, and Windows XP.

What would be the best solution? :confused:

---

### Post by PriceChild on 2011-02-04
I don't think there is a "solution".... just "the right answer for you".

If Ubuntu meets requirements 7 doesn't, install Ubuntu.
If 7 meets requirements Ubuntu doesn't, install 7.

If neither meet your requirements, install both?

[B]HOWEVER...

[/B]A better way forward (for us on these forums) would be for you to try to do everything in Ubuntu and ask questions when you can't figure out how to do something... e.g. "why can't i sync my ipod", "how do i burn this cd" If you do that, we'll probably have more useful answers.

---

### Post by ?#Yhf%*&amp; on 2011-02-04
I guess what I'm asking is this:

Is Windows 7 as prone to viruses as previous versions of Windows?

:confused::confused::confused:

---

### Post by MrRichard on 2011-02-04
> **Corbin052198 said:**
> I'm planning on getting a netbook soon (probably in May), and the model I want (Asus EEE PC 1001PX-EU17-BK) comes with Windows 7 Starter. Should I keep Windows 7, install Ubuntu 11.04, or dual-boot?

I have already found intructions on how to dual boot the way I want, and how to change the wallpaper in Windows 7 Starter. :p I also already have experiance with Ubuntu, Unity 3D, and Windows XP.

What would be the best solution? :confused:

 Sometimes, it's a bit tricky to install the network drivers in Ubuntu, so I wouldn't dive right into Ubuntu if you're unsure. My suggestion is to dualboot Windows and Ubuntu. After a week or so of use, choose your favorite OS and delete the other.

As PriceChild said, you can always post questions here and we'll try our best to resolve any issues. :popcorn:

---

### Post by philinux on 2011-02-04
Any version of windows can get get a virus as thats the OS they are targeted at.

Windows Security Essentials package seems to do a good job and it's free.

This is what I did on my Acer 1410.

Got rid of all tria/crap ware. Defragged twice. Then shrank the partition with win 7's utility. Installed easybcd to handle booting in case machine had to go back under warranty. Just makes it easier. 

Then installed ubuntu to spare space and installed Grub to the partition not the MBR. Ubuntu just worked with everthing and wireless was flawless.

Pointing easybcd at ubuntu is a doddle.

Nice dual boot setup. I use Ubuntu 99% and win 7 for silverlight based websites like sky.

---

### Post by ?#Yhf%*&amp; on 2011-02-04
> **MrRichard said:**
> Sometimes, it's a bit tricky to install the network drivers in Ubuntu, so I wouldn't dive right into Ubuntu if you're unsure. My suggestion is to dualboot Windows and Ubuntu. After a week or so of use, choose your favorite OS and delete the other.

As PriceChild said, you can always post questions here and we'll try our best to resolve any issues. :popcorn:

Thanks for the suggestion. I just looked it up, and the netbook I mentioned in the first post is supported by Ubuntu 10.04, if you upgrade the kernel. So I'm guessing Ubuntu 10.10 or 11.04 should be supported, with their newer kernels and all. :p

---

### Post by Topsiho on 2011-02-04
You ask: "Is Windows 7 as prone to viruses as previous versions of Windows?". The answer is: ***as*** prone, is difficult to say. Maybe less, maybe more. But it certainly is prone to viruses.

If that is your criterium, then get rid of Windows, which, as a starter kit, is crippled anyway. Windows except for the most expensive version, is crippleware. But: if disk space is sufficient to have both, you could alo make room to install Ubuntu (I think 10.04.1 is the best) alongside Windows, and use both OS's, learning how to use Ubuntu in the meantime, and going to love it.

The problem is: when you buy electric or electronic equipment usually there are only Windows drivers and programs for it, sometimes for Apple too, and only rarely Linux. So it's handy to still have Windows around.
But: then you also have to maintain Windows, and to my experience that's really a slow and aggravating process. And what you maintain is only Windows, and not (at the same time) the applications.

It's up to you :)

See also the advisories on the secunia site, for Windows and arbitrary linuxes. It's an eye opener, if there ever was one.

Topsiho

---

### Post by SeijiSensei on 2011-02-04
Might I suggest booting the LiveCD on the machine and seeing whether you can do what you need with Ubuntu?  (You'll need an external CDROM to do this.)

My daughter's Asus 1201N runs Win7 and Lucid in a dual-boot environment.  If it weren't for the annoying proprietary wifi network at her college, she'd be using the Ubuntu side most of the time.

---

### Post by ajgreeny on 2011-02-04
> **SeijiSensei said:**
> Might I suggest booting the LiveCD on the machine and seeing whether you can do what you need with Ubuntu?  (You'll need an external CDROM to do this.)

My daughter's Asus 1201N runs Win7 and Lucid in a dual-boot environment.  If it weren't for the annoying proprietary wifi network at her college, she'd be using the Ubuntu side most of the time.
You don't have to use a live CD and an external CD drive, you can also use a live USB; that's the way most ubuntu OSs are installed to netbooks, so making the USB will not be time wasted if you decide to install later after trying it live.

---

### Post by The Linux Cynic on 2011-02-04
I dual-boot Windows 7 and Ubuntu 10.10 (not the netbook remix) on my Asus 1201N netbook.

My verdict:
The netbook is faster with Windows 7, but for my purposes, I prefer to use Ubuntu as I am more familiar with it and I don't want to figure out how to do my day-to-day tasks with Windows.

As for viruses, I've never had any trouble with Win7. Be careful out there.

---

### Post by SeijiSensei on 2011-02-04
> **ajgreeny said:**
> You don't have to use a live CD and an external CD drive, you can also use a live USB

I thought that might be the case, but not knowing, I chose to make a more conservative post.  I'm pretty sure we used the CD for my daughter's machine since we'd bought both devices together.

---

### Post by drewsus on 2011-02-04
> **SeijiSensei said:**
> I thought that might be the case, but not knowing, I chose to make a more conservative post.  I'm pretty sure we used the CD for my daughter's machine since we'd bought both devices together.

[LiLi for Windows: the easiest way to try Linux]("http://www.omgubuntu.co.uk/2011/02/lili-for-windows-the-easiest-way-to-try-linux/")



I recommend a dualboot. That is what I have with my Acer Aspire One. If you need tips/help with partitioning, setting up burg (Graphical GRUB) etc ask.

---

### Post by pshooter on 2011-02-04
> **drewsus said:**
> [LiLi for Windows: the easiest way to try Linux]("http://www.omgubuntu.co.uk/2011/02/lili-for-windows-the-easiest-way-to-try-linux/")
 
 
 
I recommend a dualboot. That is what I have with my Acer Aspire One. If you need tips/help with partitioning, setting up burg (Graphical GRUB) etc ask.
 
help? i am trying to get win7 and ubuntu to work together on a laptop. i had win7 all installed and working, then i installed ubuntu next to it, but it only boots ubuntu and there is no option to boot win7. what did i do wrong?
 
bb

---

### Post by ?#Yhf%*&amp; on 2011-02-04
Thanks for all of your suggestions. I have made a bootable USB of Ubuntu 10.10 and tried it on my dad's netbook. Wifi works, so I was able to try Google Chronum, Unity, Opera, and Firefox.

If I can get better battery life with Ubuntu on my future netbook, consider it a fully linux netbook.

---

### Post by hakermania on 2011-02-04
Who dared to do such a comparison? Windows should be replaced with BEEEEEP, as it is an insult!
So, it should be WindoBEEEEEEP!

---

### Post by Acidpunk on 2011-02-04
> **Corbin052198 said:**
> Thanks for all of your suggestions. I have made a bootable USB of Ubuntu 10.10 and tried it on my dad's netbook. Wifi works, so I was able to try Google Chronum, Unity, Opera, and Firefox.

If I can get better battery life with Ubuntu on my future netbook, consider it a fully linux netbook.

I doubt that will happen just quite yet, though I may be wrong but from everything I've read. Windows unfortunately still owns battery performance wise due to driver optimisation.

---

