---
title: "Memory/Swap usage."
date: 2006-03-18
forum: General Help
---

### Post by sprinkles on 2006-03-18
Hello all,
I've recently installed Ubuntu on my machine in dual boot with Windows 2000 (Although to be honest, I haven't used Windows since I got my modem working under Ubuntu!).

I have a query about the memory usage. In Windows, the memory usage is all over the place, but in Ubuntu it seems to stay constant.

I have enclosed a graph from the System Monitor to show what I mean.

I appreciate any answers.

---

### Post by powder on 2006-03-18
Looks normal to me. :)

---

### Post by Jucato on 2006-03-18
Would you care to elaborate what you mean by "all over the place" and "constant"?
Oh, and Windows and Linux use different memory models and ways of using memory, so it's perfectly normal if they "seem" not to behave similarly.

---

### Post by sprinkles on 2006-03-18
Well, in Windows the memory usage never stays the same, it can go up to full memory usage, then drop back down in the space of about 5 seconds. In Ubuntu the memory usage just stays the same all of the time.

---

### Post by arctic on 2006-03-18
Linux machines tend to use all RAM you have.. Some of it is actually used by apps, the rest is cached for other tasks and will be freed/redirected to other apps if needed. Give Linux 1 GB RAM and it will use 1 GB. Give it 256 MB and it will use 256 MB. Windows will only use parts of the RAM and will free it later, but it has some "historical" problems with freeing RAM again later. (One reason for the famous BSOD). This is why your Windows system will tell you that it uses e.g. 50%, then 40%, then 74% of your RAM while Linux will tell you all the time that it uses almost 100% of your RAM.

RAM is usually installed for being used, not for not-being-used, right?

---

### Post by Pathfinder007 on 2007-07-12
You said Linux system always use 100% of the physical memory, but on the screenshot above, it's clearly showing that the physical memory is not 100% used and yet there are some SWAP usage there. I've also noticed this on my own Ubuntu system. 
I'd like to know the reason for this. 
Is there some kind of memory management setting that needs to be configured?

Even more strangely, as I attempted to open more applications, like openoffice.org 2.0 and a PDF file, the physical memory usage actually went down while the swap usage increased, and the harddrive kept working, don't what it is doing. I think there is definitely something wrong with my setup.
I have a 256mb DDR PC2100 memory and P4m 1.8Ghz laptop running Edgy.

---

### Post by Ozeuss on 2007-07-12
that graph from the system monitor shows the used memory by applications, not the cached. if you add the system monitor applet to the panel, it will show you both. you might also use "free" in the terminal that will show you your total memory usage. in your case, the apps use up about 60% of memory, and another 39% is probably cached for later use.
i'm pretty sure that if you open more memory hungry apps or close them down you will see a change, although linux use memory in a much more efficient way (lot less "frenzied" than windows).

linux has a attribute of "swappiness" that choses whether to use swap for memory (i.e, the harddrive), or the ram. the default in ubuntu is 60 (vm.swappiness, goes from 0=no swap to 100). since you don't have that much ram, i stick with the default, and not worry about your memory performance cause it seems fine.

---

### Post by Pathfinder007 on 2007-07-12
How do I see and edit this swappiness thing?

---

### Post by Ozeuss on 2007-07-12
```
cat /proc/sys/vm/swappiness
```
to find out your swappiness.
to change it for your session:
```
sysctl -w vm.swappiness=[number from 0 to 100]
```
If you want to chane it permanentyl:
```
sudo gedit /etc/sysctl.conf
```
and change it:
vm.swappiness = 70


again, the default in ubuntu is probably the one that suits you best, tweak with care.

---

### Post by Pathfinder007 on 2007-07-12
Ye, I will just have a look at it, not touching anything.

---

