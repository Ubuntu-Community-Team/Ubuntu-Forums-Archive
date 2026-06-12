---
title: "Graphics out of place?"
date: 2010-12-05
forum: General Help
---

### Post by J4M13N on 2010-12-05
I've come back to ubuntu (yesterday) after switching back to windows for quite some time, everything was installed and running fine, but I had a message come up about my graphics card.

It had two install options, one said recommended next to it, so I went with that one as I'm not really 'advanced' with linux, I'm still a beginner.

Everything appeared fine and I switched off my computer for a bit, then turned it back on, and on the boot (the part what says ubuntu 10.10) it had suddenly became larger and really blocky, (like an 8bit graphics card). 

Now a few of my icons appear to be out of place, I've attached a screenshot so hopefully somebody can help me on how to resolve this,

(Top right corner my account name, bottom left show desktop, top right wifi has a bit cut off)

[URL="http://img707.imageshack.us/i/screenshotkpo.png/"]http://yfrog.com/jnscreenshotkpop
[/URL]

---

### Post by coffeecat on 2010-12-05
> **J4M13N said:**
> Everything appeared fine and I switched off my computer for a bit, then turned it back on, and on the boot (the part what says ubuntu 10.10) it had suddenly became larger and really blocky, (like an 8bit graphics card). 

That's called the Plymouth splash screen. What you describe is  a known issue with the nvidia and ATI proprietary drivers one of which  is what you've almost certainly installed. There are alleged workarounds for the nvidia driver. There may or may not be workarounds for the proprietary ATI (fglrx) driver, but my preferred one is to uninstall it. :wink: For many ATI cards you're better of with the default open-source driver. I'm posting from a machine with a Radeon HD4350 using the OS driver and I get all the flashy compiz effects I want. Post details of your graphics card and we can take it from there.

> **J4M13N said:**
>  Now a few of my icons appear to be out of place, I've attached a screenshot so hopefully somebody can help me on how to resolve this,

That may or may not be related to the proprietary driver. I've seen something similar in one of my installs but I can't remember what/if I did about it. Does the corruption of the icons survive a reboot or logging out and in again?

By the way, when posting an image, it's better to use the forum thumbnail facility. Under the message box, you'll find a 'Manage Attachments' button. You can upload an image and it will appear as a clickable thumbnail in your post.

---

### Post by J4M13N on 2010-12-05
> **coffeecat said:**
> That's called the Plymouth splash screen. What you describe is  a known issue with the nvidia and ATI proprietary drivers one of which  is what you've almost certainly installed. There are alleged workarounds for the nvidia driver. There may or may not be workarounds for the proprietary ATI (fglrx) driver, but my preferred one is to uninstall it. :wink: For many ATI cards you're better of with the default open-source driver. I'm posting from a machine with a Radeon HD4350 using the OS driver and I get all the flashy compiz effects I want. Post details of your graphics card and we can take it from there.



That may or may not be related to the proprietary driver. I've seen something similar in one of my installs but I can't remember what/if I did about it. Does the corruption of the icons survive a reboot or logging out and in again?

By the way, when posting an image, it's better to use the forum thumbnail facility. Under the message box, you'll find a 'Manage Attachments' button. You can upload an image and it will appear as a clickable thumbnail in your post.
Thanks for your reply :)

My graphics card is a Nvidia Geforce 8400GS 512MB GDDR2. I've tried rebooting several times and everything's still the same sadly. 

Thanks for that tip I'll use it next time :)

---

### Post by coffeecat on 2010-12-05
> **J4M13N said:**
> My graphics card is a Nvidia Geforce 8400GS 512MB GDDR2. I've tried rebooting several times and everything's still the same sadly. 

I use the  8400GS card on my secondary machine but I use the default open-source nouveau driver - with which you get an uncorrupted Plymouth screen.

I really don't know whether the panel icon problem is down to the proprietary driver but it sounds as though it might be. Before you try my suggestion below (if you want to try it), go to System > Administration. Somewhere in there you should be able to find the nvidia control panel. See if there are any settings in there that might help. If not, what I suggest is to uninstall the proprietary nvidia driver using System > Administration > Additional Drivers and then reboot. That will take you back to the nouveau driver and you will see a proper Plymouth. If your upper panel is now OK, then that means the proprietary driver was the problem.

However, that leaves you with no compiz effects. If you want to get compiz with the nouveau driver, simply install the package libgl1-mesa-dri-experimental. Note the 'experimental' in the name though. I use it on my secondary machine and haven't had any problems so far, but you might.

**EDIT:** forgot to add. Of course, if you want 3d acceleration for gaming you probably do need the proprietary driver.

---

### Post by J4M13N on 2010-12-05
> **coffeecat said:**
> I use the  8400GS card on my secondary machine but I use the default open-source nouveau driver - with which you get an uncorrupted Plymouth screen.

I really don't know whether the panel icon problem is down to the proprietary driver but it sounds as though it might be. Before you try my suggestion below (if you want to try it), go to System > Administration. Somewhere in there you should be able to find the nvidia control panel. See if there are any settings in there that might help. If not, what I suggest is to uninstall the proprietary nvidia driver using System > Administration > Additional Drivers and then reboot. That will take you back to the nouveau driver and you will see a proper Plymouth. If your upper panel is now OK, then that means the proprietary driver was the problem.

However, that leaves you with no compiz effects. If you want to get compiz with the nouveau driver, simply install the package libgl1-mesa-dri-experimental. Note the 'experimental' in the name though. I use it on my secondary machine and haven't had any problems so far, but you might.

**EDIT:** forgot to add. Of course, if you want 3d acceleration for gaming you probably do need the proprietary driver.
Thanks :)

Everything is back to normal now xD

---

### Post by coffeecat on 2010-12-05
> **J4M13N said:**
> Everything is back to normal now xD

I'm glad to hear it. :)

Could you please definitely confirm that the panel icons are OK with the nouveau driver? That's an important observation. I've not seen this as a reported problem on the forums - I may have missed relevant threads - but it would useful to know about.

Also, have you tried the package libgl1-mesa-dri-experimental? Do your windows wobble, and your cube spin? :wink:

---

### Post by cascade9 on 2010-12-05
> **coffeecat said:**
> **EDIT:** forgot to add. Of course, if you want 3d acceleration for gaming you probably do need the proprietary driver.

Dont forget you'll need the proprietary driver for VDPAU as well. Not that most people 'need' VDPAU but its nice to move to video playing loads to the GPU from the CPU.

---

