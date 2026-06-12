---
title: "Can't Find drivers!"
date: 2010-07-26
forum: General Help
---

### Post by the_file on 2010-07-26
There is a laptop that I want to get that has the ATI Mobility Radeon    4100 and I cannot find it under ATI's driver downloads for any operating   system.
 
 Look for yourself [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
 select notebook, then readeon, then 4100 series, for ANY operating   system, it doesen't have a driver for it.
 
 The first question is:
 Were is the linux driver for the 4100, and the second, if there is NO   propriatary driver installed, will x take full use of the video   hardware, or will it be capped and won't work to its fullest potential   that it has?.

---

### Post by dv3500ea on 2010-07-26
It's better to install drivers from System -> Administration -> Hardware Drivers.

If nothing shows up, the driver can be found here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-7-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-7-x86.x86_64.run")

---

### Post by ve3tru on 2010-07-26
Fist off a propriatary driver doesn't mean that its better.
It means the code is hidden, and they wont let you see it, computers are not stand alone systems they integrate with various hardware and multiple software.Without being (open source) this can be difficult and sometimes impossible. Without doing a lot of research I found that a driver is in your repository so you should be able to install it no prob.
I think you will find most of the time installing drivers in Linux is easy compared to Winblows.

---

### Post by the_file on 2010-07-26
> **dv3500ea said:**
> It's better to install drivers from System -> Administration -> Hardware Drivers.

If nothing shows up, the driver can be found here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-7-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-7-x86.x86_64.run)

Does it support ATI Mobility Radeon 4100?. I only posted this because I want to buy the laptop, but if I can't take advantage of the graphics card, then compiz will suck so I much rather find a different one that has a propriatary driver written.

> **ve3tru said:**
> Fist off a propriatary driver doesn't mean that its better.
It means the code is hidden, and they wont let you see it, computers are  not stand alone systems they integrate with various hardware and  multiple software.Without being (open source) this can be difficult and  sometimes impossible. Without doing a lot of research I found that a  driver is in your repository so you should be able to install it no  prob.
I think you will find most of the time installing drivers in Linux is easy compared to Winblows.

Well actually I find installing video card drivers much easier in XP SP3 since they are very available. But does it mean that only propriatary drivers can take full advantage of the video rendering hardware?. Or does X already take full advantage and the full capabilities of the video rendering capabilities that the graphics card offers. Besides I like the catalist control center that Ati has which is really nice.

---

### Post by dv3500ea on 2010-07-27
> **the_file said:**
> Does it support ATI Mobility Radeon 4100?. 
Yes, but once you've installed ubuntu, you are better off going into the Hardware Drivers to install it rather than using the link. Only use the link if, for some reason, nothing shows up in Hardware Drivers.

---

