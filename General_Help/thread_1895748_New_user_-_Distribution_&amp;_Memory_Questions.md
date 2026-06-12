---
title: "New user - Distribution &amp; Memory Questions"
date: 2011-12-15
forum: General Help
---

### Post by mjf108 on 2011-12-15
Hi everyone,
 
Apart from a few 'test-drives' from a CD in the past, I've never used a linux-based OS before - but I want to give it a try. I'm about to get a netbook with (what I believe are) decent specs. I was therefore considering, putting in 4gb of RAM and dual-booting it with Ubuntu or similar. My questions:
 
1) Which distribution would you recommend? I was considering Xubuntu as I thought it may be a bit quicker on a netbook, but are there any recommendations? Will Ubuntu work fine?
 
2) Will the 32-bit versions support 4gb (even on the other distros?) Do Xubuntu etc have 64-bit versions?
 
Any other information or help would be massively appreciated. I'm aware that I'm coming across as quite thick on some of these matters but I'm doing my best to get to grips with this stuff.
 
Thanks,
 
Merlin

---

### Post by Mark Phelps on 2011-12-15
As a general rule, more system memory is better -- even though, with 32-bit OS, you're only going to be able to use about 3+ GB of memory.  Installing 64-bit will use all the memory, but it's not really any faster than 32-bit.

Your major problems with a netbook, like with any laptop, is that the manufacturers pair a customized BIOS with customized hardware with customized drivers -- the latter of which often present problems in Linux distros where such drivers are not available.

Since the hardware detection is essentially the same across the *buntu variants, my suggestion is to try all of them -- using unetbootin to create a USB stick of each -- and see which one you like the best.  

One limiting factor is likely to be the video chipset on the netbook.  As long as it's not one of the infamous switchable graphics chipsets (Intel/ATI or Intel/Nvidia), you should be able to get desktop graphics OK.  By trying each variant in LiveCD mode (even though it's a USB), you will also see how well they detect and install the drivers for network access and audio.

---

### Post by grahammechanical on 2011-12-15
It is not stupid to research the possibilities of what you want to do.

If you tell us what this netbook actually is, perhaps providing a link to the website advertising this product, then you may find that some here are already using that product. They can share their experiences.

Here are some areas that I suggest that you look into.

1) Is the CPU 64bit? If so, then why install a 32bit OS?

2) If the CPU is 32bit, then does the 32bit OS come with a PAE kernel built in? Without a PAE 32bit kernel you will not be able to use more than 3GB of RAM. So, if you want 4GB of RAM then look for a 64bit CPU and use a 64bit OS.

3) What video/graphic adapter does the netbook have? Will there be issues getting the full capabilities of the graphic adapter working in the OS?

4) What OS will come pre-installed on this netbook? What issues will there be dual booting with this pre-installed OS?

5) How much storage does the netbook have and of what type?

It is better to find out these things in advance, as you are wanting to do, then to go ahead and mess things up or waste your money by getting the wrong product.

Regards

---

### Post by mjf108 on 2011-12-16
Thanks for the replies. The netbook is the Toshiba NB550D - I've put some of the specs I could find at the bottom of the page.
 
It comes pre-installed with Windows Starter 7 - 32 bit, but was considering quickly replacing this with regular Windows 7 - 32 bit (don't have a copy of 64 bit, and not forking out) and then dual booting with Ubuntu. I'm not desperate to get every last bit of the 4gb RAM out of it but obviously the more the better. I've read the 32 bit/64 bit threads on here and I guess i'll just have to try them both out.
 
With regards to drivers and graphics, I admit I'm not too knowledgeable. I'll try live-CD runs as you suggested and see if it all works. Are there things which I won't be able to test in this mode?
 
I'm almost certain the CPU is 64-bit but am having problems finding anywhere that explicitly states it. Is there an easy way of looking this up?
 
Thanks again!
 
 
[LEFT][COLOR=#000000]*Specs:*[/COLOR][/LEFT]
 
[LEFT][COLOR=#000000]Processor and memory Processor: AMD Fusion C-50 [/COLOR]
[COLOR=#000000]Motherboard chipset: AMD Fusion [/COLOR]
[COLOR=#000000]Memory type: DDR3 [/COLOR][/LEFT]
 

[COLOR=#000000][LEFT][COLOR=#000000]Graphics chipset: AMD Radeon HD 6250 [/COLOR]
[LEFT][COLOR=#000000]Graphics card RAM: 256MB [/COLOR][/LEFT]
 

[COLOR=#000000][LEFT][COLOR=#000000]Capacity: 250GB [/COLOR]
[LEFT][COLOR=#000000]Spindle speed: 5,400RPM [/COLOR]
[COLOR=#000000]Internal disk interface: SATA/300 [/COLOR]
[COLOR=#000000]Hard disk: Toshiba MK2565GSXN[/COLOR][/LEFT]
 

[COLOR=#000000][LEFT][COLOR=#000000]Operating system: Windows 7 Starter 32-bit [/COLOR]
[LEFT][COLOR=#000000]OS family: Windows 7 [/COLOR]
[COLOR=#000000]Recovery method: Recovery partition[/COLOR][/LEFT]
[/COLOR]
[/LEFT]
[COLOR=#000000]
[/COLOR][/COLOR]
[/LEFT]
[COLOR=#000000]
[/COLOR][/COLOR]
[/LEFT]
[COLOR=#000000]
[/COLOR]

---

### Post by tears of the river on 2011-12-16
with those specs you should definetly go for ubuntu 11.10 as it will work quite fine. dont consider ubuntu to be similar to windows as it is much lighter and should work perfectly

---

### Post by 3rdalbum on 2011-12-16
That whole class of AMD CPU supports 64-bit. Don't even bother with 32-bit; most Linux users have been using 64-bit for years without drama. You're not restricted by low RAM so go for 64-bit.

Regular Ubuntu 11.10 will work just fine based only on your netbook's specification. I use it on my netbook, which is not as fast or modern as yours; and mine only has 1 GiB of RAM.

There's always the chance that there will be some hardware in your computer that's not compatible with Ubuntu; for example, some up-to-the-minute wifi cards won't be supported yet, or you might not have reliable suspend or hibernate. But give it a go and see how well it works.

---

