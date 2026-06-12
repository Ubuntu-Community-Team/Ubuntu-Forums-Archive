---
title: "Radeon HD 4850 having troubles with recommended 3rd party drivers"
date: 2009-07-11
forum: General Help
---

### Post by fwaokda on 2009-07-11
The Graphic Card I have is this...
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127370](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127370)

After installing ubuntu I had no problems but Ubuntu showed me I could download 3rd party drivers for it to support 3d support if I remember correctly.  I tried this but everything after restarting ran extremely slow, buggy, and some stuff just didn't ever open or didn't display right.

How can I fix this? Thanks for any tips, advice, fixes!

---

### Post by CaptainMark on 2009-07-11
For newer cards the ati propietary driver is better. 3d support is okay, i had my ati  card for all of 2months before i got rid of it.

---

### Post by fwaokda on 2009-07-11
> **CaptainMark said:**
> For newer cards the ati propietary driver is better. 3d support is okay, i had my ati  card for all of 2months before i got rid of it.

Where do I find/install this? OR is it the one that I'm probably currently using?

---

### Post by fwaokda on 2009-07-11
I've found this one, [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

I think this is what you were referring to so I'm going to try it out and I'll post back with my findings. Thanks again.

---

### Post by fwaokda on 2009-07-11
Update: I installed the drivers located there and they seem to work but I couldn't get dual monitors to work or the right resolution for one of the monitors to work. If your running one monitor perhaps it works well.  If you try this option and you get black monitor screens when booting up, then restart go into recovery mode and then choose the last option in that menu to fix graphic problems and then go to the root cmd prompt and type in: 'aticonfig --initial -f'  

That'll get you back in. Then for uninstalling if you choose to do that follow these instructions:

1 Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.

2 With superuser permissions, enter the command "sh ./fglrx-uninstall.sh".

3 Reboot your system.

Well, if anyone else has another thing I could try please post... thanks!

---

### Post by nice_like_rice on 2009-07-11
Weird I just posted just a minute ago with a question on my hd4850.. anyway mine works perfectly, not very helpful advice, but I can tell you the driver I have under system->administration->hardware drivers.

It is the "ATI/AMD proprietary FGLRX graphics driver", I'm afraid it was many months ago and I can't remember having any problems installing it.

(I am using a single monitor setup, will soon try with two)

david

---

### Post by fwaokda on 2009-07-12
> **nice_like_rice said:**
> Weird I just posted just a minute ago with a question on my hd4850.. anyway mine works perfectly, not very helpful advice, but I can tell you the driver I have under system->administration->hardware drivers.

It is the "ATI/AMD proprietary FGLRX graphics driver", I'm afraid it was many months ago and I can't remember having any problems installing it.

(I am using a single monitor setup, will soon try with two)

david

Thanks for the info, I'm going to look into some other methods this morning people have been recommending.  I think the dual monitor setup is what is causing my problems.

---

### Post by fwaokda on 2009-07-15
I've found that the problem I was having after activating the ones in Hardware Drivers was due to the xorg maxing out at 100% of the cpu.  To get around this I had to update the drivers through Update Manager. I added a repo to Software Sources prior to updating so not sure if it was included in that or not.  Hope that helps anyone else having problems.

---

### Post by Technospyder on 2009-07-18
Sounds like you are having similiar problems that I am having.  Using a 4870 myself and finally got the old drives out.  Were you ever able to find a solution to your Radeon problems?  If so, how did you fix it?

---

