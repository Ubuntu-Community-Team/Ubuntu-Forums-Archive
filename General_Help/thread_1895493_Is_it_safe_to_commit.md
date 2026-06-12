---
title: "Is it safe to commit?"
date: 2011-12-14
forum: General Help
---

### Post by Onael on 2011-12-14
Hi y'all,

I finally got a new laptop and I'm eager to get back on Ubuntu! My one question (for now) lol, is has there been any problems reported when installing the latest Ubuntu after Win7 on a 64bit HP laptop?

Thank you.

---

### Post by josephmills on 2011-12-14
> **Onael said:**
> Hi y'all,

I finally got a new laptop and I'm eager to get back on Ubuntu! My one question (for now) lol, is has there been any problems reported when installing the latest Ubuntu after Win7 on a 64bit HP laptop?

Thank you.

By there latest do you mean daily builds or 11.10 ?

---

### Post by bluexrider on 2011-12-14
> **Onael said:**
> Hi y'all,

I finally got a new laptop and I'm eager to get back on Ubuntu! My one question (for now) lol, is has there been any problems reported when installing the latest Ubuntu after Win7 on a 64bit HP laptop?

Thank you.
There are always some sort of issues I cannot speak for Ubuntu but download at your own risk.

---

### Post by hg088 on 2011-12-14
you should be fine with ubuntu, but i wouldnt erase w7, after all u paid for it

id just reduce the w7 partition to make room for ubuntu

---

### Post by Onael on 2011-12-14
I understand there's always issues. I assume that the latest 11.10 LTS is safe to install. I'd have to backup my system of course before I tried. I don't have any specific concerns. I'm just looking for testimonials, I guess.

---

### Post by hg088 on 2011-12-14
when u are in windows use partition wizard to reduce the partition and then install ubuntu

---

### Post by sammiev on 2011-12-14
If you have a full backup of your OS, then I would move right on to 12.04 as you can always return to your backup quickly. :) 12.04 is more for testers but I must add I haven't had any problems at all to date. :)

---

### Post by Jerry N on 2011-12-14
> **Onael said:**
> Hi y'all,

I finally got a new laptop and I'm eager to get back on Ubuntu! My one question (for now) lol, is has there been any problems reported when installing the latest Ubuntu after Win7 on a 64bit HP laptop?  

Assuming you want to dual boot Win 7 and Ubuntu, the major problem is that typically HP laptops use all 4 of the permissible primary partitions. This has been discussed at length many times in these forums. When you shrink the main (biggest) Win 7 partition to make space, be sure to use the Win 7 disk management tool but do not use the Win 7 disk management tool to create a new partition.  You could also use a WUBI install and avoid partitioning problems but in my biased opinion WUBI is a very poor way to run Ubuntu.

Jerry

---

### Post by Hylas de Niall on 2011-12-15
> **sammiev said:**
> If you have a full backup of your OS, then I would move right on to 12.04 as you can always return to your backup quickly. :) 12.04 is more for testers but I must add I haven't had any problems at all to date. :)


I had kernel panics and no desktop when i tried the 12.04 alpha on my little 11.10 netbook, though it loaded up well enough on the desktop machine.
The aplha is deffo still alpha in behaviour IMHO and i wouldn't recommend it as main system just yet.

---

### Post by claracc on 2011-12-15
> Onael wrote:
Re: Is it safe to commit?
I understand there's always issues. I assume that the latest 11.10 LTS is safe to install

ubuntu 11.10 is not a long term support distro. The stable LTS is 10.04 lucid lynx and the next one will be 12.04 precise pangolin but it is in its alfa release for now.

---

### Post by Mark Phelps on 2011-12-15
Ubuntu 11.10 presents with serious kernel problems on some laptops that makes them overheat and drains the battery quickly.

The only real way to find out if yours is one of those affected is to boot from a desktop CD (or use unetbooting to make a bootable USB) -- and see for yourself.

IF you do decide to dual-boot, be sure to follow the advice of others regarding using the Win7 Disk Management utility to shrink Win7. Do not allow the Ubuntu installer to do this for you.  That risks corrupting Win7 and rendering it unbootable.

And, I would advise strongly AGAINST jumping into an alpha release of anything -- unless you want to spend your time dealing with crashes and bugs.

---

### Post by rsvancara on 2011-12-15
I have an HP Pavilion dv7 laptop and I will tell you about my issues.

1.  Wireless fails to start back up after the laptop goes to sleep on kernel 2.6.38.  This is probably the most annoying problem.  Some folks claim turning off wireless-n fixes the problem.  

2.  Back light controls do not work under Linux.  So you further reduce your battery life.  My laptop has a Intel I7 processor so I do not expect great life anyways.

3.  The laptop has two graphics cards.  There is (not from what i can see) a way to turn this feature off unless you really want to dig into grub and look into vga-switheroo.  

4.  The laptop has a ATI video card, which already has horrible Linux support as ATI fails at producing solid Linux drivers.  Open source drivers work great.  Hopefully at some point, they will get the hint and just let the community maintain their drivers.

------------------
[http://www.knowyourlinux.com/]("http://knowyourlinux.com/content/ssh-rest-us")

---

### Post by Mark Phelps on 2011-12-15
> **rsvancara said:**
> 3.  The laptop has two graphics cards.  There is (not from what i can see) a way to turn this feature off unless you really want to dig into grub and look into vga-switheroo.  

Is the info in the link below what you're referring to?

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by Simian Man on 2011-12-15
It's never "safe" to use Linux if by "safe" you mean everything (or anything) will work.  You could install only to find that Ubuntu has transformed your laptop into a very expensive paperweight.  Just make/keep a recovery disk and/or dual-boot.

---

