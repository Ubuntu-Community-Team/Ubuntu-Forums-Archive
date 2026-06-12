---
title: "Need help installing Ubuntu,,,"
date: 2011-05-16
forum: General Help
---

### Post by VRock on 2011-05-16
Hello, I'm sorry if this is in the wrong forum...

I'm trying to install Ubuntu onto an older computer. It has 1GB of RAM.

I couldn't get the disc to boot up on start up so I got Ubuntu to fix that for me with the handy feature it has on the installation disc.

However, when trying to boot up Ubuntu from the disc, it gives me this error:

try (hd0,0): NTSF5: error: "prefix" is not set

Waiting for about two minutes seems to ignore this, however, as it goes straight into the Ubuntu start up screen. However, after being there for a moment the loading bar stops loading and it seems to stop working in general.

Anyone know what's going on?

---

### Post by Rubi1200 on 2011-05-17
Hi and welcome to the forums :-)

I am trying to understand what is going on here:

1. what graphics card do you have installed?

2. are you trying to install **inside **Windows with the Wubi installer?


> I couldn't get the disc to boot up on start up so I got Ubuntu to fix that for me with the handy feature it has on the installation disc.

Could you explain what this means please.

How did you burn the image to CD, which software did you use?

Thanks.

---

### Post by VRock on 2011-05-18
> **Rubi1200 said:**
> 
1. what graphics card do you have installed?


Intel Pentium D CPU 2.80GHz
 ATI Radeon HD 2400 Series
 1 GB RAM
 
 If  you need to know anymore info just ask but those are my CPU, Graphics  and RAM info. They're all pretty old.

> **Rubi1200 said:**
> 
2. are you trying to install **inside **Windows with the Wubi installer?


Well, what I wanted to do was have the disc inside the computer so that it'll boot up Ubuntu when I turned it on but it just wasn't giving me the option to boot from the disc so...

> **Rubi1200 said:**
> 
Could you explain what this means please.


...I chose the option from the installation disc that said it'll help if I can't boot from the dsic from start up. It's the third option on the disc:

-Reboot Now
-I want to manually reboot Later
-Help me to boot from CD <-- That Option

However, doing that produces the scenario I described above.

I also tried installing it like a Windows program and that seems to work... for about 80-90% of the  installation process (within Ubuntu). At this point, a black screen  pops up with a ton of information on it but it's more or less just a  huge error screen. When I try to boot up Ubuntu again it works fine  until I log in... where it just gives me the background and that's it.

I also tried Kubuntu but it doesn't even go beyond the Start-Up screen.

This is pretty damn  frustrating... It just seems to me that this computer can't be  configured to use Linux on it. It must be the mother board, which I'm  sure is pretty old.                                                                                          

> **Rubi1200 said:**
> 
How did you burn the image to CD, which software did you use?


I used Daemon Tools to act as a virtual CD drive and then I use Nero to copy the virtual CD to an actual CD.

I'm downloading Linux Mint and Xubuntu now but I don't think they'll produce much better results... in the end, I'd much rather have Ubuntu anyway though.

---

### Post by 4Orbs on 2011-05-18
You can find answers in [This How-To]("http://www.psychocats.net/ubuntu/iso").

---

### Post by -kg- on 2011-05-18
I'm having serious problems wrapping my mind around exactly what it is you're trying to do, and how you're going about it.

> I'm trying to install Ubuntu onto an older computer. It has 1GB of RAM....

...what I wanted to do was have the disc inside the computer so that it'll boot up Ubuntu when I turned it on but it just wasn't giving me the option to boot from the disc...

I can understand this part, but...

> ...I couldn't get the disc to boot up on start up so I got Ubuntu to fix that for me with the handy feature it has on the installation disc....

..I chose the option from the installation disc that said it'll help if I can't boot from the dsic from start up. It's the third option on the disc:

-Reboot Now
-I want to manually reboot Later
-Help me to boot from CD <-- That Option

This is what has me completely confused.  If you couldn't boot to the installation disk, then how did you boot to the installation disk to get to that menu (which, BTW, I've never seen in the 3 years I've been dealing with Ubuntu)?  At exactly what point do you get that menu?  And if you can't boot from the CD, how do you get there?

Are you trying to do something like "installing" Ubuntu to a CD or DVD, to be run like a regular installation, except on a CD/DVD/Flash Drive?  Are you trying to install it on your hard drive?

If you're trying to "install" Ubuntu on a CD/DVD, then I'm not sure whether you can accomplish that.  There's barely enough memory on a DVD, and if you want persistence, you'd need to use a DVD-R/W to accomplish it.

The installation disk itself is a "Live CD", which means you can run Ubuntu from the "installation disk", though it will be limited in what you can do with it.  Much better to use a persistent installation to a Flash drive (of sufficient size...say 8 GB, or larger if possible) if that's what you're trying to accomplish.

I've had a thought....did you download the Live CD version of Ubuntu, or did you download the Alternate Install CD?  If you downloaded the Alternate Install version, it doesn't have a desktop, per se...you have to install it to your hard drive or a flash or external USB drive.  Since it's an older machine, you might not be able to boot from a USB device, in which case the PlOP bootloader could be of help.

If you were trying to install it on your internal hard drive, it should be straightforward.  If you can't boot to your CD, then it should be impossible to find a "menu" on the CD, since you can't boot to it in the first place.  I'm just not understanding exactly what it is you're trying to accomplish and how you're going about it.

---

### Post by VRock on 2011-05-18
I'll explain it more throroghly...

I want to clarify that I do indeed have the Ubuntu iso burned onto a disc. I don't need to know how to do that.

I am trying to install it onto my hard drive. I only have one hard drive and I can't partition it because Windows XP does not have these features. I would personally love to format my computer completely and just install Ubuntu fresh on it but I don't know if I can do that.

I cannot run the install disc upon boot time. The option simply does not come up. It goes straight into Windows XP.

On the Installation Disc, it tells me it can help me with the installation using the "Help me to boot from CD" option. It adds the option to boot Ubuntu instead of Windows XP on boot up.

However, doing this option, when I select Ubuntu it just gives me the Ubuntu start-up screen and it doesn't let me progress.

When I do the option to install Ubuntu using the "Install inside Windows" option, it goes through the installation and when I boot up Ubuntu, it goes through the normal installation progress until about 80-90% through it gives me a black screen with a huge error. The next time I boot up Ubuntu it goes past the start up screen, to the log in screen. After I log in, it just hangs and does not proceed to the desktop.

I am not sure how much more detailed I can describe this. I don't want to install Ubuntu onto a disc and I don't need to burn it into a disc I already have one. I just simply want to dual-boot Ubuntu alongside Windows XP!

---

### Post by Wim Sturkenboom on 2011-05-18
> **VRock said:**
> I cannot run the install disc upon boot time. The option simply does not come up. It goes straight into Windows XP.
Did you change the boot order in the BIOS? This sounds like the CD is not detected as bootable or the boot order is wrong.
> **VRock said:**
> I want to clarify that I do indeed have the Ubuntu iso burned onto a disc. I don't need to know how to do that.
Because it is not detected as bootable (assuming the bootorder is correct), how did you burn the CD? As a file or as an image?


> **VRock said:**
> On the Installation Disc, it tells me it can help me with the installation using the "Help me to boot from CD" option. It adds the option to boot Ubuntu instead of Windows XP on boot up.

However, doing this option, when I select Ubuntu it just gives me the Ubuntu start-up screen and it doesn't let me progress.

When I do the option to install Ubuntu using the "Install inside Windows" option, it goes through the installation and when I boot up Ubuntu, it goes through the normal installation progress until about 80-90% through it gives me a black screen with a huge error. The next time I boot up Ubuntu it goes past the start up screen, to the log in screen. After I log in, it just hangs and does not proceed to the desktop.

I am not sure how much more detailed I can describe this. I don't want to install Ubuntu onto a disc and I don't need to burn it into a disc I already have one. I just simply want to dual-boot Ubuntu alongside Windows XP!
OK, I think I'm getting it now. When in Windows, you see the disk and try to install from within windows. If so, that refers to a Wubi install. It will install Ubuntu inside Windows (not a real dual boot in my opinion). And from this, I think that you indeed burned as an image. **So is your boot order set correctly?**

Can't help you with Wubi, I'm sure others can.

Just a warning
Assuming this is a live CD, run it first from CD to make sure that your video is supported. Nothing more annoying than ending up with a black screen.

---

### Post by -kg- on 2011-05-18
OK, that clarifies it a bit.

Given that your computer is an older one, you need to change a few things in your BIOS settings.  Apparently, your BIOS is not set up to check your CD drive for a bootable CD before your hard drive.  This is often set because of speed considerations in the boot process.

There are various methods of accessing BIOS on different computers.  Some use the "Del" key; some use another key; and some use one or another of the Function keys.  Whichever your computer uses, go into your BIOS Setup (it should show you during the boot-up process, usually at the bottom of your screen).

Once there, you are going to need to change your "Boot Sequence."  By what you've indicated, your Boot Sequence is set to check your hard drive first.  That's why you can't boot to your CD...it checks the hard drive first, and since it finds a boot loader there, it checks no further.  You need to change it to check your CD ROM drive first so that, finding a boot-able CD, it will boot to that.

Once you've changed your Boot Sequence, you should be able to boot to the CD, and you're in like flint!  Any other issues, just post!

---

