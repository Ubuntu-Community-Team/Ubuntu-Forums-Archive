---
title: "Laptop getting very hot under Ubuntu"
date: 2011-12-20
forum: General Help
---

### Post by thacursedpie on 2011-12-20
Dear all,

I am running into problems when trying to use my laptop for university work (molecular modelling, to be precise).

When I run a simulation under Ubuntu (which is very demanding), my laptop gets very hot (> 90C). Of course this is a no-go, I don't want to have my CPU fried.

Under Windows however, my laptop runs a lot cooler. Idle temp is about 45C, compared to 68C for Ubuntu! I also have no difficulty running demanding applications (such as Skyrim) under Windows, it just doesn't get as hot as under Ubuntu!

When the CPU heats up the fan *does* spin, but I have no way of knowing if it is spinning at max rpm.

Do you guys have any idea? I searched around and found out that the 2.6.38 Linux kernel has a regression in powerconsumption and also increased heat production, could this be the cause (I'm running Ubuntu 11.04 IIRC, at least I'm sure I'm running kernel version 2.6.38-11)

Thanks in advance!

---

### Post by BC59 on 2011-12-20
Possible solutions are the following:
Install the proprietary graphic drivers.
Install [Jupiter]("http://http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html")
Install [kernel 3.0.0]("http://http://kernel.ubuntu.com/~kernel-ppa/mainline/")

---

### Post by thacursedpie on 2011-12-20
Thanks for your quick reply!

I've tried all your suggestions:

* Install proprierty drivers
This one just seems to be screwed up for me. X won't launch properly and it comes up with a bunch of errors on boot.

Retried installing it, but then Ubuntu just launched into a CLI, no GUI at all... Weird. Then trying 'X' crashed too.

* Install Kernel 3.0.0
Done, everything's working correctly. Though I don't notice a difference regarding the temps.

* Install Jupiter
Done, this app is amazing. The powersaver profile is a life saver. Under 'performance' mode, temps do not get as high as they used to get, so that helps, too. I'm going to see if I can edit the configuration files to get a profile in-between "power saver" and  "high performance".

Alas, the problem still isn't resolved, but turning down the performance helps, of course. Thanks :).

If anyone has any tips to get rid of the underlying cause (or any idea how to get the proprierty graphics drivers working), I'd be very grateful :).

---

### Post by BC59 on 2011-12-20
What type is your graphics card?

---

### Post by MartijnNL on 2011-12-20
Also have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1897430](http://ubuntuforums.org/showthread.php?t=1897430)

---

### Post by thacursedpie on 2011-12-20
Thanks for your quick reply!

I've tried all your suggestions:

* Install proprierty drivers
This one just seems to be screwed up for me. X won't launch properly and it comes up with a bunch of errors on boot.

Retried installing it, but then Ubuntu just launched into a CLI, no GUI at all... Weird. Then trying 'X' crashed too.

* Install Kernel 3.0.0
Done, everything's working correctly. Though I don't notice a difference regarding the temps.

* Install Jupiter
Done, this app is amazing. The powersaver profile is a life saver. Under 'performance' mode, temps do not get as high as they used to get, so that helps, too. I'm going to see if I can edit the configuration files to get a profile in-between "power saver" and  "high performance".

Alas, the problem still isn't resolved, but turning down the performance helps, of course. Thanks :).

If anyone has any tips to get rid of the underlying cause (or any idea how to get the proprierty graphics drivers working), I'd be very grateful :).

---

### Post by davidryderuk on 2011-12-20
Are you still using the same laptop you posted about in June (the MSI cx620 laptop)? Perhaps you could look at a guide on using HybridGraphics in Ubuntu:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Having two graphics cards running together will generate more heat. You might need to pick one, and make sure it's properly enabled, with the other one switched off, before trying to install extra drivers.

p.s. My Macbook idles at about 48°C, but reaches 85°C when running flat out. Since my fan definitely isn't running at maximum, does anyone know what a safe temperature range is for a modern post-2010 processor?

---

### Post by Mark Phelps on 2011-12-20
> **thacursedpie said:**
>  ...If anyone has any tips to get rid of the underlying cause ...
The underlying cause is a bug in the Linux kernel -- which the kernel developers are working to resolve.

---

### Post by BC59 on 2011-12-20
There is a workaround for this [bug]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html"), but not sure if it's working

---

### Post by thacursedpie on 2011-12-20
@BC59
Switchable graphics:
Intel Integrated graphics 
+
Ati Radeon HD5470

@davidryderuk
Yes I'm still using the same laptop. Thank you for noticing and pointing out that webpage! vga_switcheroo doesn't seem to work for me though. While my kernel was compiled to allow it, it isn't enabled (/sys/kernel/debug/vgaswitcheroo/switch doesn't exist).

I haven't got a clue how to get that file. The webpage you linked to said to boot with 'modeset=1'  and remove the 'nomodeset' parameter, if it was present. I did as suggested, but it didn't change a thing!

I did give the acpi_call method a try, and it worked, a bit! I followed all the steps outlined and it allowed me to switch off my discrete graphics card. I wasn't able to stop my integrated graphics card though. (removed the entry relevant for my discrete card from the acpi_call list, ran again, but none of the tries was successful :( ).

Still, it helps a lot with saving power, so thanks a lot!

@Mark Phelps , BC59
Hm, I see. I tried the workaround, but to no avail.


@all
Disabling my ATI card and limiting to "High Performance" using Jupiter allows me to run the modulation computations without overheating (too much, it still gets very hot: 87C, :O). I'm not sure how healthy this is for my CPU...

So it still heats up, but not to as rediculous high temperatures. My guess is this is because of the underclocking Jupiter does, though other factors, such as stopping my ATI card, might also be helping

---

