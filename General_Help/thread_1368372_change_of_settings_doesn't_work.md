---
title: "change of settings doesn't work"
date: 2009-12-30
forum: General Help
---

### Post by povar81 on 2009-12-30
I'm a beginner in linux so far, and after installing ubuntu 9.10 I have encountered several problems: 
1. I'd like windows to load by default - I've installed bootup manager and changed settings there - but it didn't change anything: when I boot up ubuntu is still by default. 
2. Futhermore, the changes I make in System-Administration-NVIDIA X server settings are don't work either, and I have to change them back after every rebooting. 
3. I don't really like the display settings, but I don't know how to change them correctly - by default, the system boots up in max. resolution (1280x1024), but it's not convinient for me - I change to 1024x768, but it looks worse, a bit, emm..., unclear, nondistinct. 

Please help me, especially with the first problem - is there some alternative utility or something? 
Thank you.

---

### Post by howefield on 2009-12-30
> **povar81 said:**
> 1. I'd like windows to load by default - I've installed bootup manager and changed settings there...

What do you mean by "bootup manager" ? If you are not talking about startupmanager, then try that, install with Synaptic.

 
> 2. Futhermore, the changes I make in System-Administration-NVIDIA X server settings are don't work either, and I have to change them back after every rebooting.

Try opening nvidia-settings as admin, ie, go to Applications > Accessories > Terminal and type into it

```
gksu nvidia-settings
```

This will allow you to save the changes you make.

---

### Post by jamesisin on 2009-12-30
So, this is a dual boot system?  Which OS did you install first, Windows or Ubuntu?

---

### Post by povar81 on 2009-12-30
> **jamesisin said:**
> So, this is a dual boot system?  Which OS did you install first, Windows or Ubuntu?
Yes, I've installed ubuntu after windows, and I'd like windows to boot up by default so far.

---

### Post by povar81 on 2009-12-30
> **howefield said:**
> What do you mean by "bootup manager" ? If you are not talking about startupmanager, then try that, install with Synaptic.

 


Try opening nvidia-settings as admin, ie, go to Applications > Accessories > Terminal and type into it

```
gksu nvidia-settings
```This will allow you to save the changes you make.

Oh, yes, I'm sorry I confused bootup with startup - it's startup manager that doesn't work properly for some reason.
I've tried gksu nvidia-settings - changed settings - and once again - no result after reboot.

---

### Post by jamesisin on 2009-12-30
When you power up the machine, Grub loads and then Ubuntu starts?

---

### Post by povar81 on 2009-12-31
> **jamesisin said:**
> When you power up the machine, Grub loads and then Ubuntu starts?
Yes, exactly.

---

### Post by povar81 on 2009-12-31
something's probably wrong - I've accidentally installed bootup manager and now when I tried to uninstall it - it freezed at 30% and didn't move any further. 
Oh, by the way, Happy New Year to everyone! 
I hope you can find some time to help me, thank you.

---

### Post by povar81 on 2010-01-02
Nothing helps! What else can I do? 
Do I have to reinstall ubuntu? 
See I've tried ubuntu - then Mint, then Mandriva 2010, and then I decided that ubuntu is the best, the most convinient among them, so I've installed it again - and it turned out to be so problematic this time. 
I think I did everything right during the installation - formatted to ext4 every time.

---

### Post by HappyFeet on 2010-01-02
You will need to edit grub2 to get windows to boot first. [Here]("https://help.ubuntu.com/community/Grub2") is some documentation on grub2.

---

### Post by povar81 on 2010-01-02
Thanks, but I've already fixed the 1st problem by reinstalling ubuntu, still the other two problems remain - I have to change my resolution every time after reboot, please tell me how can I fix that?

---

### Post by povar81 on 2010-01-02
Yes! I fixed the second one by creating the conf file with sudo nvidia-xconfig. Now the changes I make can finally be save up. 

Well, now there's only the last one left - it's not too critical, but still I'd like to know what is the best resolution and frequency and maybe some other adjustments for my samsung '19 monitor.

---

