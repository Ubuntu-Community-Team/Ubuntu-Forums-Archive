---
title: "Lenovo Thinkpad X61S 7667 CTO Graphic Driver"
date: 2011-12-27
forum: General Help
---

### Post by HaZeTJ on 2011-12-27
hi there, I'm new to this kind of OS, i have run windows all my life but had some trouble with it's performance..
So i went on and tried out this Ubuntu but i have a slight problem, I haven't used Linux before so know nothing about this..

My problem is that Ubuntu doesn't show my graphic driver is shown as "unknown" and my graphic-state?? (my system is in danish so don't know if it is correct) is shown as "Standard-state" ? ?

the system is a little bit slow, but that is proberly becaus of missing compatible drivers ? ?

Now for my questing, how do i get the correct drivers so it will run as it should ?
I'm not high tech geek so i can get confused and ask stupid questions :P

Thanks in advance

EDIT: Look at post #[**3**]("http://ubuntuforums.org/showpost.php?p=11571820&postcount=3")

---

### Post by mikewhatever on 2011-12-28
Generally, there are no special made drivers for Lenovo graphics, Dell audio, or HP wireless, simply because computer vendors do not make these components, but rather use stock hardware by Intel, Nvidia, Realtek, etc, and re-distribute their drivers. This makes the search for 'Lenovo XYZ graphics driver meaningless, because there is no such thing.

If your Lenovo has an Intel GPU, the driver for it is included (as most other drivers). Nvidia and AMD provide closed source drivers, which can be installed through the Additional Drivers utility.

Hope that somewhat helps, and if not, provide some info about the hardware. The output of 'lspci -knn | grep VGA -A1' would be a good start.

---

### Post by HaZeTJ on 2011-12-29
> **mikewhatever said:**
> Generally, there are no special made drivers for Lenovo graphics, Dell audio, or HP wireless, simply because computer vendors do not make these components, but rather use stock hardware by Intel, Nvidia, Realtek, etc, and re-distribute their drivers. This makes the search for 'Lenovo XYZ graphics driver meaningless, because there is no such thing.

If your Lenovo has an Intel GPU, the driver for it is included (as most other drivers). Nvidia and AMD provide closed source drivers, which can be installed through the Additional Drivers utility.

Hope that somewhat helps, and if not, provide some info about the hardware. The output of 'lspci -knn | grep VGA -A1' would be a good start.

Thanks, I've pasted it below
VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
    Subsystem: Lenovo T61 [17aa:20b5]
Hmm just re-installed ubuntu to fix the mess i made :P
But now i cant get ubuntu to recognizing my graphic card again, just had it working..

but i have tryed sudo intelTool in terminal and it says the following:
> 
Intel CPU: Family 6, Model f
Intel Northbridge: 8086:2a00 (PM965)
Intel Southbridge: 8086:2811 (unknown)
I then tried sudo varinfo and this came:
> 
libva: libva version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/i965_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
The laptop lag's all the time and the system hangs..

I would past all my sys info but don't know how to obtain them in Linux :S

I have another problem to with Java, in betsson.dk i can't se the "login filed" where i should be able to write my user name and password.. In my bank the Java plug-in works perfectly. But not on betsson.. No messages come up it just shows a blank field where the login should be.. ??
As said before i just reinstalled so i have'nt installed any Java yet, so what Java should i install ? ?

EDIT: Here is a small video that show you the problem i have
[http://www.youtube.com/watch?v=nccqmYHKGj4](http://www.youtube.com/watch?v=nccqmYHKGj4) hope it can help a bit, if you want any other info just type me msg and the command i should use then I throw it on here to..

---

