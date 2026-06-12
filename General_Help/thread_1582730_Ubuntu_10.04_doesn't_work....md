---
title: "Ubuntu 10.04 doesn't work..."
date: 2010-09-26
forum: General Help
---

### Post by melrokz on 2010-09-26
Ubuntu 10.04 boots into a blank screen! The problem seems to be my video card: Intel 845GL.
I actually get a screen with this message written all over it:
'Could not write bytes: broken pipe'
Even Windows 7 doesn't work on this card.
I'm not in a position to upgrade my PC.
I've tried the workarounds in 'Lucidi8xxFreezes', to no avail.
Is there any other solution to it?

---

### Post by harrismh777 on 2010-09-26
What video resolution are you trying?  Stick to something like 1024x768 till you figure this out.

Also, what kernel options are you using. Try turning of ACPI  and APCI and see if that helps.  Also,

... have you tried booting the live CD... 10.04?  9.04?  8.04?   do any of the live CDs work.

Obviously if there is a hardware problem with the card you're going to need to upgrade...

:popcorn:

---

### Post by melrokz on 2010-09-26
* Ya, It's time I got a new system ;-)
* Yes, the live cd's all work.
* Plz tell me what to add to the kernel line in /boot/grub/grub.cfg
* Resolution is 1366x768, 60 Hz. Got a BENQ LED monitor.

---

### Post by harrismh777 on 2010-09-27
On live CD boot-up set the resolution to 1024x768.

Turn off automatic power management stuff... acpi apci & other...  use the options menu to select how to turn them off. Load ubuntu with those options.

Sounds like you have an xorg problem that could be resolved once the machine is loaded and running.

When the machine boots into the black screen (with no login) press:

   ctrl-alt-F1   

... does the machine go into a black screen terminal, and can you logon?

If so, then you definitely have an xorg problem that can most likely be resolved with load options or xorg config.

---

### Post by melrokz on 2010-09-27
dmesg o/p: main stuff
> 
* [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
* render error detected, EIR: 0x00000000
* [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5
* [drm:i915_gem_idle] *ERROR* hardware wedged

What should I understand from this? Is it a hardware problem?

---

### Post by pluckypigeon on 2010-10-18
I got that all the time. Maybe you could try and use the Vesa driver. 

Add this to xorg.conf. Performance will probably regress though

```


Section "Device"
    Identifier     "845g"
    Driver         "vesa"
EndSection


```

---

### Post by melrokz on 2010-10-18
Got this one fixed with Ubuntu 10.10! Thanks!

---

### Post by Themotorman on 2010-12-06
> **melrokz said:**
> Got this one fixed with Ubuntu 10.10! Thanks!

I have a laptop Dell D505 with the Intel 845 chip set for video. It will not work with anything past Ubuntu 9.04. I have so far  (June 2010 )tried almost everything that has been suggested . If you have now a working system with 10.10 and the intel chip please tell me, in detail, how you managed to do this. My Dell works great and I do not either want to buy a new one or dump this one into the endless pile of useful but unusable electronics. 

Thankyou

---

