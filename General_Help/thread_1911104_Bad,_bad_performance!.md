---
title: "Bad, bad performance!"
date: 2012-01-18
forum: General Help
---

### Post by Jaxke on 2012-01-18
Hello! I hope this is the right place to ask this...

Okay, I installed Ubuntu to my new laptop(Acer 5750) with Wubi installer. So far, I'm having one major problem, awful performance.

Basically, if I try to transfer files from a folder to another(for example), and browse the web at the same time, my computer will freeze(oddly I can still move my mouse..). The only thing I can do is hold the power button, and make my computer shut down. 

What might be the problem? I tried to diagnosis the problem, but I did not find anything. I tried changing my file manager, changing desktop environments(I guess that's the right term...).

I know Ubuntu can do better. Even Windows is faster now.

And my specs are: 6GB RAM(DDR3), Intel Core i5 2,4GHz(dual-core), so that should be more than enough.

I was also wondering, that if I reinstall Ubuntu, is there any application that would backup all my programs and their data(Android has those, and it's only a phone...)

Thank you!(I know my English sucks, but I hope you understand :P )

---

### Post by mastablasta on 2012-01-18
> **Jaxke said:**
>  
And my specs are: 6GB RAM(DDR3), Intel Core i5 2,4GHz(dual-core), so that should be more than enough.
 
not enough. What graphics card are you using? did you install proprietary graphics drivers (if needed)? Also how much disk you gave the install? Wubi is not the best way to go , but still it should't be so slow.
 
> 
I was also wondering, that if I reinstall Ubuntu, is there any application that would backup all my programs and their data(Android has those, and it's only a phone...)
 
There is plenty. what kind of backup you want to be doing? baremetal? bit by bit? image of OS backup? Timed backup ? very simple GUI interface backup?!?! you name it you go it.

---

### Post by aromo on 2012-01-18
> **Jaxke said:**
> Basically, if I try to transfer files from a folder to another(for example), and browse the web at the same time, my computer will freeze(oddly I can still move my mouse..).

If you can do stuff before it freezes, I recommend you run [FONT="Courier New"]system-monitor[/FONT] and check the memory usage (alternatively run [FONT="Courier New"]free -m[/FONT] on a terminal session).  That may point you on the right direction.

---

### Post by Scott Baker on 2012-01-18
Quick question here. What version of Ubuntu are you attempting to run? Versions up to 11.04 run relatively quick, 11.10 is a bit slower based on its graphical enhancements. Keep in mind also, that a WUBI install has a tendency to run a bit slower, because it's still treated like any other piece of software that's installed in the Windows environment.

---

### Post by mlentink on 2012-01-18
> **Scott Baker said:**
> Keep in mind also, that a WUBI install has a tendency to run a bit slower, ***because it's still treated like any other piece of software that's installed in the Windows environment***.
My emphasis.
How do you figure that?

---

### Post by soekarmana on 2012-01-18
for better performance install ubuntu directly to disk (dual boot)

wubi will always be slower than dual boot especially on disk activity (copy file), because wubi uses virtual disk inside NTFS partition

---

### Post by Scott Baker on 2012-01-18
Just a quick clarification (although I've already been beaten to the draw). When Ubuntu is installed through WUBI, it behaves just like any other programs that are installed into Windoze. It is running in the Windows environment, instead of on its own. ( Think of Ubuntu running in WUBI/Windoze like widows programs behave when run through WINE in Ubuntu ). It works, but you're trying to actually run 2 OSs at the same time ( so to speak ) hence the decline in performance. :-k

**As a final thought here. Some Linux users see these same types of performance issues when running software through a program like virtual box.

---

### Post by coldjeanz on 2012-01-18
I installed Wubi last week and experienced the same problem. It takes FOREVER for data transfer (like from external HDD) and downloading a file with dropbox takes so long that I actually can't use the computer at all while its doing it. If I try to do anything it will just freeze up.

Since I like Ubuntu I want to keep using it but yeah Wubi is not that great. I would do a real dual boot if I could but I don't have time to learn how to do it right now and if something goes wrong I certainly won't have time to fix it. I wish someone could make a video on how to migrate your Wubi data to a real dual boot.

---

### Post by Paqman on 2012-01-18
> **Scott Baker said:**
> Just a quick clarification (although I've already been beaten to the draw). When Ubuntu is installed through WUBI, it behaves just like any other programs that are installed into Windoze. It is running in the Windows environment, instead of on its own. ( Think of Ubuntu running in WUBI/Windoze like widows programs behave when run through WINE in Ubuntu ). It works, but you're trying to actually run 2 OSs at the same time ( so to speak ) hence the decline in performance. :-k


That's not correct. Wubi is not virtualisation. When you're booted into Ubuntu that was installed by Wubi, no parts of Windows are running.

All Wubi does is install Ubuntu onto a virtual partition that happens to be located on the Windows NTFS partition. While it's true that this will cause disk I/O to suffer a slight performance hit, the effect is so small you're unlikely to notice it.

Sluggish performance is usually a problem with the graphics card, not Wubi.

**Jaxke**: You should open Additional Drivers and install any drivers for your graphics card that it offers.

---

### Post by mastablasta on 2012-01-19
> **coldjeanz said:**
> Since I like Ubuntu I want to keep using it but yeah Wubi is not that great. I would do a real dual boot if I could but I don't have time to learn how to do it right now and if something goes wrong I certainly won't have time to fix it. I wish someone could make a video on how to migrate your Wubi data to a real dual boot.
 
it is really easy.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
i bet there are youtube videos...
first back up your wubi data (if you have any in your wubi install) 
 
then you need to defragment the disk at least 2 times (second time will be faster), do a checkdisk afterwards. That way all your windows data is stuck on one place on the disk (the beginning). so when you create an empty partition (with the windows disk manager) it will likely be on emtpy part of disk with no chunks of data there. thus your windows data is safe.
 
then you are off to install. you install on that empty space, select default options according to your needs (ubuntu will make the necessary partitions within that empty space) and that's it. 
 
there rest is more or less same as in wubi.

---

### Post by tkabir11 on 2012-01-19
> **Paqman said:**
> That's not correct. Wubi is not virtualisation. When you're booted into Ubuntu that was installed by Wubi, no parts of Windows are running.

All Wubi does is install Ubuntu onto a virtual partition that happens to be located on the Windows NTFS partition. While it's true that this will cause disk I/O to suffer a slight performance hit, the effect is so small you're unlikely to notice it.

Sluggish performance is usually a problem with the graphics card, not Wubi.

**Jaxke**: You should open Additional Drivers and install any drivers for your graphics card that it offers.

+1. I also don't believe OPs performance problems has got anything to do with Wubi. I also had Ubuntu 11.10 on Wubi alongside a very old sluggish Windows Vista when I was first trying it out- and Ubuntu was performing smooth like a dawg ;)

---

