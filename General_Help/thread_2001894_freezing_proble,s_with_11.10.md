---
title: "freezing proble,s with 11.10"
date: 2012-06-11
forum: General Help
---

### Post by mj360 on 2012-06-11
for some reason ubuntu freezes up when i download things online, it will freeze for maybe 30 sec when start working but freeze over and over until the download is done. i thought it was just firefox but it does it with chromium too. so i maybe the nvidia drive is what peoblem so i tried unstall the nvidia drive  but the nvidia x server settings is still on it but when i go to additional drivers it shows it's not install so i think this have something to do with my problem. can anyone help ?

---

### Post by Bucky Ball on 2012-06-11
Does the machine work okay apart from when you're downloading? Are you talking about streaming vid/music (Youtube or other) or downloading a file, if you follow me?

---

### Post by mj360 on 2012-06-11
> **Bucky Ball said:**
> Does the machine work okay apart from when you're downloading? Are you talking about streaming vid/music (Youtube or other) or downloading a file, if you follow me?
everything else works fine it just when download is when the problems happens.

---

### Post by Bucky Ball on 2012-06-11
Downloading a file or streaming content?

If it is the former, I can't see how the cause of your problems would be graphics drivers. If it is the latter I would suggest you need to check you have the correct plugins and codecs installed. ;)

---

### Post by mj360 on 2012-06-11
> **Bucky Ball said:**
> Downloading a file or streaming content?

If it is the former, I can't see how the cause of your problems would be graphics drivers. If it is the latter I would suggest you need to check you have the correct plugins and codecs installed. ;)
it's downloading a file, streaming is fine no problems it's when downloading anything the problem

---

### Post by mj360 on 2012-06-12
anybody ? please ?

---

### Post by gn0m3boy on 2012-06-12
May be an 'X-Freeze' issue related to High CPU Due to Software Rasterizing of a particular action...in your case downloading something as a dialogue box tends to pop-up in Firefox with the progress line or in Chrome with the suppressed pop-up still has a circle progress graphic - that's just a stab in the dark so to speak as to why it freezes up...the GPU throws the work to the CPU instead of doing the work itself for whatever reason and the CPU spikes and temporarily freezes the system due to over load...

Try reverting to an earlier kernel...Hold down the left-shift key during re-boot.  This should give you a grub menu and you can select an earlier kernel to use. When you get on the desktop, try downloading something and see if you experience the same issue...

ref:

 [[COLOR="Blue"]https://wiki.ubuntu.com/X/Troubleshooting/Freeze[/COLOR]]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze")

 [[COLOR="Blue"]https://wiki.ubuntu.com/X/Troubleshooting/HighCPU[/COLOR]]("https://wiki.ubuntu.com/X/Troubleshooting/HighCPU")

---

### Post by mj360 on 2012-06-12
> **gn0m3boy said:**
> May be an 'X-Freeze' issue related to High CPU Due to Software Rasterizing of a particular action...in your case downloading something as a dialogue box tends to pop-up in Firefox with the progress line or in Chrome with the suppressed pop-up still has a circle progress graphic - that's just a stab in the dark so to speak as to why it freezes up...the GPU throws the work to the CPU instead of doing the work itself for whatever reason and the CPU spikes and temporarily freezes the system due to over load...

Try reverting to an earlier kernel...Hold down the left-shift key during re-boot.  This should give you a grub menu and you can select an earlier kernel to use. When you get on the desktop, try downloading something and see if you experience the same issue...

ref:

 [[COLOR=Blue]https://wiki.ubuntu.com/X/Troubleshooting/Freeze[/COLOR]]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze")

 [[COLOR=Blue]https://wiki.ubuntu.com/X/Troubleshooting/HighCPU[/COLOR]]("https://wiki.ubuntu.com/X/Troubleshooting/HighCPU")

when i look at the previous kernels it show only 3.0.0.20  and only shows the same kernels in the previous kernels as well what should i do?

---

### Post by gn0m3boy on 2012-06-12
> **mj360 said:**
> when i look at the previous kernels it show only 3.0.0.20  and only shows the same kernels in the previous kernels as well what should i do?

Follow the directions in the 2 provided links and start troubleshooting...Start with the X troubleshooting link and show your results...also give some details on:
Your nvidia hardware - is it on-board or a card?  What model?
What drivers are you using for that card?  
Run  System Monitor and launch Chrome next to it and try downloading something - What peeks as far as memory usage goes?
Details, details, we need the details... ;)

---

### Post by mj360 on 2012-06-12
> **gn0m3boy said:**
> Follow the directions in the 2 provided links and start troubleshooting...Start with the X troubleshooting link and show your results...also give some details on:
Your nvidia hardware - is it on-board or a card?  What model?
What drivers are you using for that card?  
Run  System Monitor and launch Chrome next to it and try downloading something - What peeks as far as memory usage goes?
Details, details, we need the details... ;)
i'm sorry but i didn't understand the X troubleshooting link well,can you walk me through it ? on-board nvidia geforce 9200 and 4gb of ram. i don't know what driver is on cause system info it say unknown but i know it;s one that say recommended and i Run  System Monitor and launch Chrome and downloaded a 115mb video, the memory peek at 901.8mib atfer the video stop downloading it peek at 895.7

---

### Post by mj360 on 2012-06-12
also it freezes when i update ubuntu in update manager

---

### Post by mj360 on 2012-06-12
hello somebody ? anybody ?

---

