---
title: "Ubuntu 12.04 freezing just after login"
date: 2012-07-17
forum: General Help
---

### Post by mahela007 on 2012-07-17
Since yesterday, my Ubuntu system has become completely unusable. It freezes just after log in or just after I open the very first application window. The keyboard and mouse do not respond so I can't get to a Ctrl + FX terminal. The only change that I've made recently is using dual monitors. 
I have an Nvidia geforce 7100 Graphics card and the drivers are the 302.17 drivers from the X-update ppa. Everything worked well for about two boot-ups after the monitors were installed.. 
(all recent updates have been applied)
What can I do to fix this?

---

### Post by robtygart on 2012-07-17
I had the same kind of problem with Nvidia-current... But mine would not load at all. 

Right now I am using nouveau and now it works fine.

You could try a different graphic driver.

---

### Post by mahela007 on 2012-07-18
What's the procedure for doing that?

---

### Post by robtygart on 2012-07-18
> **mahela007 said:**
> What's the procedure for doing that?

```
sudo apt-get install nouveau-firmware
```

---

### Post by mahela007 on 2012-07-18
Thanks for the quick reply. 
So I don't need to worry about purging the current nvidia drivers?

---

### Post by robtygart on 2012-07-18
> **mahela007 said:**
> Thanks for the quick reply. 
So I don't need to worry about purging the current nvidia drivers?


I would! I removed mine.

---

### Post by NikTh on 2012-07-18
Hi ,
as i know nouveau driver (open source) is blacklisted when Nvidia (additional - restricted) driver is on the air. 
So you must first purge (as you mentioned) nvidia driver and after reboot , nouveau will take place again. 
You can test it by this command
```
lspci -nnk | grep -iA2 vga
```
and check what **driver is in use: **
Thanks

---

### Post by robtygart on 2012-07-18
> **NikTh said:**
> Hi ,
as i know nouveau driver (open source) is blacklisted when Nvidia (additional - restricted) driver is on the air. 
So you must first purge (as you mentioned) nvidia driver and after reboot , nouveau will take place again. 
You can test it by this command
```
lspci -nnk | grep -iA2 vga
```
and check what **driver is in use: **
Thanks

Thanks for posting Nik, I was unsure of how to go about that.

---

### Post by mahela007 on 2012-07-20
Well I tried purging the Nvidia drivers and it worked .. to an extent. I can now login to Ubuntu without it crashing. However, I only have video on my VGA monitor and there doesn't seem to be any HDMI output (to the other monitor). Also, Nouveau seems to be extremely slow .. there is significant lag when I move windows around. 

glxgears gives a frame rate for about 212
and lspci shows this :
```
00:10.0 VGA compatible controller [0300]: NVIDIA Corporation C73 [GeForce 7100 / nForce 630i] [10de:07e1] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0158]
    Kernel driver in use: nouveau

```

---

