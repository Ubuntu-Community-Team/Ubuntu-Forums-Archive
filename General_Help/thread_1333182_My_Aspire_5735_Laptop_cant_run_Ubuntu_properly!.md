---
title: "My Aspire 5735 Laptop cant run Ubuntu properly!"
date: 2009-11-21
forum: General Help
---

### Post by Insomnius on 2009-11-21
Hello, I used to use Ubuntu on my old computer about 5 months ago, but now I have a laptop, I want to use it on here, so I install it, and restart my computer, but the grub doesn't come up so I can launch ubuntu instead of Windows 7. So I try and launch the demo version from the live CD and when I get to my desktop, the graphics is all messed up, I cant see the desktop properly, its like my graphics card doesn't support ubuntu or something. If anyone could help, that would be great.
Thanks
       Insomnius

---

### Post by nastyguard on 2009-11-21
I don't really know how to fix this issue, so the best thing I can do right now is to BUMP the post.

Hope you get the help you need!

---

### Post by Insomnius on 2009-11-21
Ok, thanks for your reply :)

---

### Post by ragein on 2009-11-21
I'm quite new here so don't take anything I say too seriously.

For your graphics problems are you using a Nvidia card?  If so Ubuntu does come with Nvidia drivers but it won't install them on it's own as they arn't free software, to install them goto System - Administration - Hardware Drivers (Karmic).  I'm not sure this would work from a live cd though as it's running from a cd and doesn't have anywhere to save the data to.  If your graphics are completely screwed then you will probably have to install the drivers from a command line before you boot into gnome how to do that i'm not entirly sure so another help post would be a good place to start.


To try and fix your problems with Grub the first thing that comes to mind is did you install Ubuntu to the same hard disk as windows? If you installed to a different HDD then you will probably have to go into the BIOS and change the boot order so the computer sees the HDD with Grub on it before it sees windows and tries to boot that.  If that works you will probably want to leave that HDD as the first to boot and then look into adding windows to Grub's config unfortunately something else I can't really help you with.

Good luck

---

### Post by Insomnius on 2009-11-22
I dont have an Nvidia graphics card, and the second 1 I dont really know how to do that coz I have already tryed changing the boot menu, but I couldn't find where to change it. But thanks for the reply!

---

### Post by ragein on 2009-11-22
Unfortunately a BIOS is a right pain to help with over the internet as there are loads of different ones.

To boot into the BIOS you will need to press one of the F keys or maybe del depending upon how your laptop was set up bu the manufacturer.  The easiest way to tell is to restart the laptop and look for a "splash screen" this usually has you computers manufacturer logo on it and somewhere within it information such as

Press F12 to network boot, Press DEL to enter setup, Press F2 to choose boot device
btw i made that all up from memory it will be different on your system.

Your looking for the enter setup/bios/configuration option or maybe the boot device option (I will cover that later).

Once into the BIOS/setup/configuration screen your looking for an option like
Boot order
Boot configuration
*spends 5 minutes trying to think of other ways I have seen it worded*
Boot device
Startup options/configuration
anything else that sounds likely ;p

It could very well be hidden inside another menu make sure you look everywhere, once you find it there should be a way of selecting which HDD you boot from hard disks are generally named after their manufacturer and model for example a western digital drive might appear "WD H47463i87" or a seagate drive may appear as "Seagate cheetah b983y" if you have two then it's a possibility you installed grub onto the second one so try making that one higher in the boot order than the other.  Save your settings and reboot.

If you have a boot device option on the splash screen then try that first it will allow you to select which HDD to boot from without saving that setting.

Changing options in your BIOS could cause some real problems with your computer so the best thing to do is not change anything your not sure about and make a note of what you did change so you can undo it later.

---

### Post by Insomnius on 2009-11-23
Thankyou for your reply, I will try that after I get back from school :)
But would u know anything about my graphics problem?

---

### Post by ragein on 2009-11-23
I'm guessing by aspire 5735 you mean an Acer?  If so then it looks like it has Intel on board graphics and seeing as Intel are normally pretty good at providing open source drivers then i'm surprised it doesn't work out the box.

To be honest I don't really know what to do here, find out the exact name of your graphics majig and do some googleing with the word ubuntu tagged on the end if thats no help try making a separate thread in the hardware and laptops part of the forums.

---

