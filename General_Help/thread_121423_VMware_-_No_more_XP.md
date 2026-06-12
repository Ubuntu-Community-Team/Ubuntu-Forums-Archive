---
title: "VMware - No more XP?"
date: 2006-01-25
forum: General Help
---

### Post by Gentleman on 2006-01-25
The last half year I only used my winxp for graphical development (Adobe cs suite - Photoshop, Illustrator, Indesign, Acrobat Dist. ...)

I'm really sick of having 2 operation systems, and prefer using linux...

I would like to try VMware in ubuntu to run my needed apps,
my question: is this a good idea? - wont everything be much slower / more memory usage,... 

I would only use windows for those apps and make it as lite as possible (disable many services, no internet, no AV or Antispyware,..., no windows apps...)
Can I have something like a shared folder in vmware-windows and linux? Or is the windows installation totaly separated from linux?

I also think win2000 S4 would be a better choise than xp?

I really hope I can remove my windows partition...

---

### Post by kenweill on 2006-01-25
[QUOTE=Gentleman]The last half year I only used my winxp for graphical development (Adobe cs suite - Photoshop, Illustrator, Indesign, Acrobat Dist. ...)

I'm really sick of having 2 operation systems, and prefer using linux...

I would like to try VMware in ubuntu to run my needed apps,
my question: is this a good idea? - wont everything be much slower / more memory usage,... 

I would only use windows for those apps and make it as lite as possible (disable many services, no internet, no AV or Antispyware,..., no windows apps...)
Can I have something like a shared folder in vmware-windows and linux? Or is the windows installation totaly separated from linux?

I also think win2000 S4 would be a better choise than xp?

I really hope I can remove my windows partition...[/QUOTE]

More memory is required. 512mb or more.

I'm currently using Ubuntu 5.10 with WinXP installed under VMware Player, with 700mb+ memory.

It works fine. Its something like running Windows XP in another computer. Both can see each other when you are in a network. I use Windows XP to connect to the internet. Ubuntu for using the internet.

Before, I dual boot Windows XP and Ubuntu. Now, I only installed Ubuntu. Installed VMware and installed Windows XP. 

I don't know about Win2000. I have problems with Win98 and WinMe especially when it comes about drivers, like video and sound drivers. The device detected by WinXP runned at VMware is different than the device detected with your Ubuntu. But with Windows XP, resolution is  automatically adjusted even if you don't have the driver for your video adapter.

---

### Post by midwinter on 2006-01-25
As long as you have the memory for it, it'll work great.  

With just 512mb, Photoshop running under XP in vmplayer was useable but slow.  I bought another 512mb and now it runs perfectly.  I'll be deleting my windows partition shortly.

---

### Post by IronWolve on 2006-01-25
Might want to try some of those applications with Wine, it will run faster than vmware, and use less memory.   Check the wine site to see which apps are supported, but photoshop is, not sure about all plugins.

---

### Post by murex on 2006-01-25
I've been using Ubuntu + VMware with 1GB RAM for 6 months. Everything is working OK, speed is good and XP are usable. I use mainly GIS programs, very heavy

---

### Post by kenweill on 2006-01-25
[QUOTE=murex]I've been using Ubuntu + VMware with 1GB RAM for 6 months. Everything is working OK, speed is good and XP are usable. I use mainly GIS programs, very heavy[/QUOTE]

I'm off topic:
I too use GIS programs. ArcView GIS.

---

### Post by Gentleman on 2006-01-25
OK; I'll have 1024mb ram soon, so it can't be a problem...
Anybody tweaked XP as lite as possible? Can anyone confirm if win2000 S4 is a better choise than xp??

- Wine isn't a good solution here (only runs PS7 almost perfect)... I do have a feeling It won't be long and we can run the cs-apps on wine... (I think crossover is working on this...)

---

### Post by Marshall2day on 2006-01-25
I'm not sure about win2000 but if you want to make XP as lite as possible, check out [http://www.tweakxp.com/](http://www.tweakxp.com/) It has lots of performance tips. In my case it boots up in about 20 seconds in VMWare. Very Usable to. If you specify your home folder as a shared folder in your vm preferences, you can access it from within your vm in network places.

---

### Post by Gentleman on 2006-01-25
I thought about nlite to make XP as lite as possible... + after the setup a few tweaks with tweakxp

---

### Post by murex on 2006-01-26
Tip: I alway use the **suspend** feature in vmware, so i don't have to wait for boot :)

---

