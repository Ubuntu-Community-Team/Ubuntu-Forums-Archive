---
title: "Hardware problem?"
date: 2011-04-29
forum: General Help
---

### Post by Fbio on 2011-04-29
Ok ppl, im very begginer in Ubuntu, i started to use it 3 days ago.

I installed Ubuntu 10.10 3 days ago,  and when i installed Nvidea drivers , my computer reboots itself randomly. 

It freezes  then, after 10 seconds it reboots.


So i uninstalled it and installed Ubuntu 11.04.

But the same happens. But now it shows a black screen with some error like this:


[Hardware problem ] No human .... MDC .. decoding
[HArdware problem ]  .... message acii   


and reboots after 30 secs.  

Something like that  im going to write the error correcltly.

---

### Post by KegHead on 2011-04-29
Hi!

More info about your setup please.

KegHead

---

### Post by imthebossofme on 2011-05-02
I'm also experiencing this issue. Running dual boot with Win7 x64 on a core i5 and Asus P8P67 mobo.

I can boot in to and run windows without a problem. I can boot and install ubuntu 10.10 but the 11.04 disc throws up the same error as above.

RAM has been tested and has no errors and I will be performing diagnostics on the CPU when I get home this evening.

---

### Post by rwsmith61 on 2011-05-03
You haven't given much info to go on so here are a couple tips:

1) Are you overclocking? The first time I OC'ed my P8P67 i7-2600K with a stock CPU fan it overheated and I had similar problems. If you are then reset your BIOS (instructions are in the User Guide). There is a thread on the P8P67 for setting up lm-sensors and monitoring your system [HTML]http://ubuntuforums.org/showthread.php?t=1675550&highlight=p8p67
[/HTML]

2) Is the system stable in receovery mode (should be on the Grub menu)? 

3) Are the Nvida drivers installed correctly? Best to check in recovery mode. Check your X11 config file (if it exists) at /etc/X11/xorg.conf. 

4) Check the X logs at /var/log/Xorg.0.log and look for lines that start with (EE).

If you can get us more info and details on your set up then we can provide more detailed help. 

--bs

---

