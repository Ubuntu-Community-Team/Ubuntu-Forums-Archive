---
title: "Problems with fglrx and Ubuntu 10.10"
date: 2010-12-08
forum: General Help
---

### Post by jpr0 on 2010-12-08
I'm using Ubuntu 10.10 and my motherboard has integrated Radeon HD 4250 graphics. I'm also using the AMD fglrx proprietary driver. 

When plymouth is loading, and at the login screen (as well as during the log-out process), the display on my desktop is garbled. After I log in though, then the display seems to be okay. Sometimes, however, when I log in, I'm unable to get a resolution any higher than 1200x600 (the chipset can support up to 1920x1080). 

Is anybody else experiencing these kinds of problems with fglrx in ubuntu 10.10? Or does anybody know what I can do to try and diagnose the problem?

Thanks :)

---

### Post by dcstar on 2010-12-08
> **jpr0 said:**
> I'm using Ubuntu 10.10 and my motherboard has integrated Radeon HD 4250 graphics. I'm also using the AMD fglrx proprietary driver. 

When plymouth is loading, and at the login screen (as well as during the log-out process), the display on my desktop is garbled. After I log in though, then the display seems to be okay. Sometimes, however, when I log in, I'm unable to get a resolution any higher than 1200x600 (the chipset can support up to 1920x1080). 

Is anybody else experiencing these kinds of problems with fglrx in ubuntu 10.10? Or does anybody know what I can do to try and diagnose the problem?


Search for the many posts on Plymouth and fglrx or nvidia drivers.

---

### Post by jpr0 on 2010-12-08
> **dcstar said:**
> Search for the many posts on Plymouth and fglrx or nvidia drivers.

Well I had spent a few hours trawling google for related posts but none of these seem to be describing having a login window that's illegible. Is there a specific post you're referring to?

---

### Post by martinwebster on 2011-03-14
> **jpr0 said:**
> Well I had spent a few hours trawling google for related posts but none of these seem to be describing having a login window that's illegible. Is there a specific post you're referring to?

I thought I'd add that I'm also experiencing the same problem on an Asus M4A88TD-V EVO/USB3 motherboard using the integrated Radeon HD 4250 graphics display adaptor.

The login window displays horizontal artefacts that change when you select user and enter the password. Once logged in, the display performs as expected.

I've yet to resolve this issue. If I am successful I shall post here.

---

### Post by jpr0 on 2011-03-14
> **martinwebster said:**
> I thought I'd add that I'm also experiencing the same problem on an Asus M4A88TD-V EVO/USB3 motherboard using the integrated Radeon HD 4250 graphics display adaptor.

The login window displays horizontal artefacts that change when you select user and enter the password. Once logged in, the display performs as expected.

I've yet to resolve this issue. If I am successful I shall post here.

This is the same board that I have (and exactly the same errors). If I disable fglrx and use the drivers in the kernel, then I don't get any of those artifacts at the log-in screen. Past the log-in, everything seems fine. It was annoying enough for me to use the native graphics driver though.

---

### Post by martinwebster on 2011-03-14
> **jpr0 said:**
> This is the same board that I have (and exactly the same errors). If I disable fglrx and use the drivers in the kernel, then I don't get any of those artifacts at the log-in screen. Past the log-in, everything seems fine. It was annoying enough for me to use the native graphics driver though.

I've removed the fglrx driver for now but will revisit this when I buy a new monitor; I'm currently running an old Dell M770 CRT. Are you using a flat panel or CRT?

Another symptom is that the boot splash is displayed as text (I don't mean a text boot up just text replacing graphic and dots.) I resolved this by changing the screen resolution using StartUp-Manager. Can someone confirm that the log-in screen is displayed by Plymouth, i.e. before GDM starts? I'm guessing that this is a Plymouth issue and I'd like to pass on information to the developers.

---

### Post by jpr0 on 2011-03-14
> **martinwebster said:**
> I've removed the fglrx driver for now but will revisit this when I buy a new monitor; I'm currently running an old Dell M770 CRT. Are you using a flat panel or CRT?

Another symptom is that the boot splash is displayed as text (I don't mean a text boot up just text replacing graphic and dots.) I resolved this by changing the screen resolution using StartUp-Manager. Can someone confirm that the log-in screen is displayed by Plymouth, i.e. before GDM starts? I'm guessing that this is a Plymouth issue and I'd like to pass on information to the developers.

re: graphics during boot, I'm not sure.. it's a while since I used that driver. I'll try loading fglrx and checking next time. I'm using a flat screen, monitor, a viewsonic 22". Not sure of the exact model...

---

### Post by jpr0 on 2011-03-14
> **martinwebster said:**
> I've removed the fglrx driver for now but will revisit this when I buy a new monitor; I'm currently running an old Dell M770 CRT. Are you using a flat panel or CRT?

Another symptom is that the boot splash is displayed as text (I don't mean a text boot up just text replacing graphic and dots.) I resolved this by changing the screen resolution using StartUp-Manager. Can someone confirm that the log-in screen is displayed by Plymouth, i.e. before GDM starts? I'm guessing that this is a Plymouth issue and I'd like to pass on information to the developers.

Yeah, I get a dodgy looking spectrum-zx type boot screen.. and actually I'm having those horizontal lines everywhere even after I've logged in. For instance I can't even see what I'm typing right now. I have to force chrome to refresh the page by minimizing it and maximizing it. Panels take an eternity to "load" (i.e. have all their horizontal lines filled in), and the menu is unusable. I'm using this kernel:

2.6.35-27-generic-pae

edit: Can you check what kernel you are using? If I use the 2.6.35-27-generic-pae kernel, then fglrx spews all over the screen generally, while if I use just the 2.6.35-27-generic kenel, then I have no problems with a garbled log in screen, or with the graphics in general after log in. The only thing that persists is the ascii looking boot screen.

---

### Post by martinwebster on 2011-03-16
> **jpr0 said:**
> edit: Can you check what kernel you are using? If I use the 2.6.35-27-generic-pae kernel, then fglrx spews all over the screen generally, while if I use just the 2.6.35-27-generic kenel, then I have no problems with a garbled log in screen, or with the graphics in general after log in. The only thing that persists is the ascii looking boot screen.

I'm using 2.6.35-22-generic-pae. For the avoidance of doubt, are you saying that the problem is resolved with 2.6.35-27-generic?

---

### Post by mastablasta on 2011-03-16
similar issue on start and this is the solution that was provided to me (i use open source ATI drivers):
 
> To make the plymouth theme show on start-up enter the following into the terminal:
 
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u


---

### Post by jpr0 on 2011-03-16
> **martinwebster said:**
> I'm using 2.6.35-22-generic-pae. For the avoidance of doubt, are you saying that the problem is resolved with 2.6.35-27-generic?

Yep, the problem seems to be solved using the non-pae kernel, at least for me. Try using that kernel and see if it solves your problem. If so then I'm not sure who we should be submitting a bug report to...

---

### Post by martinwebster on 2011-03-16
> **mastablasta said:**
> similar issue on start and this is the solution that was provided to me (i use open source ATI drivers):

Unfortunately, this relates to a different issue; the problem described above only affects the proprietary ATI fglrx driver.

---

### Post by martinwebster on 2011-03-16
> **jpr0 said:**
> Yep, the problem seems to be solved using the non-pae kernel, at least for me. Try using that kernel and see if it solves your problem. If so then I'm not sure who we should be submitting a bug report to...

Thanks. Yes, I tried it and can confirm that this is a good fix. Since I've only 4GB memory there is currently no need for the PAE kernel.

---

### Post by jpr0 on 2011-03-16
> **martinwebster said:**
> Thanks. Yes, I tried it and can confirm that this is a good fix. Since I've only 4GB memory there is currently no need for the PAE kernel.

I guess we should still report it. I'm not sure where it should be reported though.

---

### Post by martinwebster on 2011-03-16
> **jpr0 said:**
> I guess we should still report it. I'm not sure where it should be reported though.

Ditto. I guess the problem could relate to either kernel, fglrx or Plymouth.

---

### Post by jpr0 on 2011-03-16
> **martinwebster said:**
> Ditto. I guess the problem could relate to either kernel, fglrx or Plymouth.

I doubt it's a plymouth problem, since the horizontal lines persist post log-in for me - they affect menus, windows, pretty much everything.

---

### Post by jpr0 on 2011-04-11
Since we're using the same motherboard - have you lost audio with recent updates? I can't get audio with this system any more...

---

### Post by martinwebster on 2011-04-12
I have no sound issues. However, I am running on Linux Mint 10 - an Ubuntu 10.10 derivative - using ALSA and PulseAudio.

---

### Post by terrydrogbar4 on 2011-04-17
I could have swore I tried sudo unmount but if you guys say it's solved I'll mark it.

---

