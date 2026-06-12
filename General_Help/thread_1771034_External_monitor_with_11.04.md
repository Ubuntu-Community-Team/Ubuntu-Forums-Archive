---
title: "External monitor with 11.04"
date: 2011-05-30
forum: General Help
---

### Post by chah on 2011-05-30
Hi all,

I'm connecting my laptop, a Sony Vaio that has WXGA:1280x800 resolution, to an external monitor that has 1280x1024 resolution. The information for the monitor's resolution came from playing with the monitor menus and having 1280x1024 as the suggested resolution, but 1024x768 as the actual signal resolution.

So I dug into the Ubuntu settings to try to change the resolution. Under the control center I found some settings for the monitor preference. Under the resolution tab, I only have 3 choices: 1024x768, 800x600 and 640x480. 

Question 1: How can I get it to display 1280x1024 so I maximize the use of my external monitor's resolution?

Question 2: Can I have my laptop screen working at 1280x800 and the external monitor at 1280x1024?

Question 3: Can I set it up so that I have one workspace on the laptop at its native resolution and one workspace on the external monitor at its native resolution?

After playing around with the "monitor preferences", I found that  I can control the settings for the internal and external screens independently, however, I'm getting some weird results when I try to change settings. For the most part, the external monitor seems to disappear at resolutions above 1024x768. Does anyone have any suggestions?

Thanks and Regards,

Kheong.

---

### Post by linuxinstalledfromhdd on 2011-05-30
If you are in Gnome, have you tried Additional Drivers yet? 

Desktop >> System >> Administration >> Additional Drivers.

Does it list any drivers for your system that can be installed there?

---

### Post by chah on 2011-05-30
> **linuxinstalledfromhdd said:**
> If you are in Gnome, have you tried Additional Drivers yet? 

Desktop >> System >> Administration >> Additional Drivers.

Does it list any drivers for your system that can be installed there?

I searched for "additional drivers" from the dash, with the external monitor plugged in, it is showing no proprietary drivers, and nothing appears in the box below for me to install.

My external monitor is HP L1950g. Do I need to go somewhere to download drivers?

---

### Post by linuxinstalledfromhdd on 2011-05-30
What is the make and model of computer? I'll try a cross reference really quick for you.

---

### Post by chah on 2011-05-30
> **linuxinstalledfromhdd said:**
> What is the make and model of computer? I'll try a cross reference really quick for you.

Thanks! It's a Sony Vaio VGN-SZ583N: 
[http://www.sony-asia.com/product/vgn-sz583n](http://www.sony-asia.com/product/vgn-sz583n)

The monitor is HP L1950g.

---

### Post by linuxinstalledfromhdd on 2011-05-30
I think I found what you need here:

[http://www.linlap.com/wiki/sony+vaio+vgn-sz+series](http://www.linlap.com/wiki/sony+vaio+vgn-sz+series)

---

### Post by chah on 2011-05-30
> **linuxinstalledfromhdd said:**
> I think I found what you need here:

[http://www.linlap.com/wiki/sony+vaio+vgn-sz+series](http://www.linlap.com/wiki/sony+vaio+vgn-sz+series)

Thanks for the link. Unfortunately, I can't seem to find any material on connecting external monitors at that page.

Here's something I find a bit strange, perhaps someone here can explain it. Ubuntu chose the default resolution as 1024x768 for both the external and internal monitors. When I go to the monitor preference and uncheck "same image on all monitors", it messes up the external monitor, the internal still works, even when I keep it at 1024x768 for both choices. 

Also, even though there is a choice of 1280x800 when I choose the laptop monitor, when I choose that option, the screen on the laptop doesn't go to 1280x800, and (as usual), the external monitor picture disappears. It makes me feel that there should be some choices elsewhere for tuning the resolutions of the monitors.

---

### Post by linuxinstalledfromhdd on 2011-05-30
Maybe this will help?
[http://www.krizka.net/2007/05/20/external-monitor-on-ubuntu/](http://www.krizka.net/2007/05/20/external-monitor-on-ubuntu/)

---

