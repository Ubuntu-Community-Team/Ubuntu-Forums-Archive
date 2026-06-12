---
title: "Is heating up of laptops with some Linux a myth?"
date: 2010-06-18
forum: General Help
---

### Post by rajn on 2010-06-18
Hi,
I have seen numerous reports of laptops heating up and the cause has been attributed to Linux. Is this a myth or is there some reality to this?
I  will appreciate if seasoned developer's respond to this  i.e., would appreciate answers which are not guesses.
Thanks

---

### Post by Chame_Wizard on 2010-06-18
The manufactures are ignorant to open source their specification documents.

It's mostly the fan btw.

---

### Post by gradinaruvasile on 2010-06-18
Laptops sometimes have customized chipsets and sometimes there are no or worse-than-Windows drivers released for them. The customizations mostly have to do with heat dissipation/power management so its normal that sometimes the laptops get hotter than in Windows in some cases.
But take in account the fact that some laptops are hot even in Windows - the older AMD processor-driven ones seem to fall in this category (dunno how the Athlon II's fare).

Newer kernels (2.6.30+) have improved power management - using proprietary drivers for nvidia and ati cards keep them cooler by using efficiently their power saving functions.

One problem is very widespread: browsing in Linux sites that contain many flash elements will increase CPU usage, leading to a hotter laptop. The flash player seem to use more cpu than in Windows on some sites (not all).

This being said, i use a Dell D630/Nvidia and the battery in Debian lasts approximately as much as in Windows (2.5-3 hours) - it doesnt get hotter than in Windows also. I have cpu load/cpu temperature applets in the taskbar and i see if something uses many cpu and act accordingly - i also disable flash by default and enable it only when i really need it on a site. Also i dont play games on it.

---

### Post by philinux on 2010-06-18
Got a 3 year old advent that is set up to dual boot. Heat, battery same in ubuntu as windows.

---

### Post by Leopardson on 2010-06-18
I have an Acer Aspire One. When I run it on windows, it gets so hot that I have to put it on a paper towel or three to keep it from burning my fingers.
When I run it in Ubuntu, the bottom of the laptop is luke warm. It is also louder. I'm not sure what is going on, but I think it has to do with the Windows drivers not running a fan/fans that Linux does. 
So far, my experience with Ubuntu on my laptop has been fantastic.

The battery time is pretty much equal. 2:07 in Ubuntu, 2:10 in Windows (Probably rounded).

---

### Post by doas777 on 2010-06-18
it depends on whether the motherboard manufacturers Advanced Power Configuration Interface (APCI) implementation is compatible with the OS's.  MS has tried in past to make APCI a windows only thing. 

My laptop for instance runs 10-20 degrees cooler running ubuntu than it does windows, just because the processor scaling is more aggressive. 

but getting APCI to work perfectly on all manufactures boards is an uphill battle, one that may not be an entirely fair fight. 
> 
[SIZE=3]*&#8220;If seems unfortunate if we do this work and get our  partners to do the work and the result is that Linux works great without  having to do the work. Maybe there is no way To avoid this problem but  it does bother me. Maybe we can define the APIs so that they work well  with NT and not the others even if they are open. Or maybe we could  patent something related to this.&#8221;*[/SIZE]--Bill Gates internal email January, 24 1999

---

### Post by ajgreeny on 2010-06-18
There is a problem also with some older ati graphic cards which use the open source ati/radeon driver.  I have an old Acer Travelmate 2200 with an ati 9000m card which seems almost to melt when running Lucid, as it gets so incredibly hot.  I tried Lucid and immediately removed it and put Karmic back on which runs cool as a cucumber.

This is something to do with the driver and 2.6.32 kernel in Lucid not being able to use KMS power management, so overheating ensues.  It is very annoying, but other than trying the 2.6.34 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/") which is supposed to have better power management ability, I have no idea what you can do about it.

I will try it sometime, but it's a trial that I am not sure I want to make at the moment, as Karmic works so well on that laptop.

---

### Post by Marlonsm on 2010-06-18
It depends on the computer.
In mine, for example, the heat and the battery are about the same in Windows 7 and in Kubuntu 10.04.

---

### Post by mindrebo on 2010-06-18
I'm using Ubuntu 10.04 LTS.  The most recent updated I got did something to interfere with my fan operation, and my Acer Aspire 5315 kept overheating.  So I went back to the older version and it works fine.  
Anyone else have that problem?  Any fixes?

---

