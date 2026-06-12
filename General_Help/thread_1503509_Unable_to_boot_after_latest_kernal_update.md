---
title: "Unable to boot after latest kernal update"
date: 2010-06-06
forum: General Help
---

### Post by dyslexicfurby on 2010-06-06
I'm a linux newbie so be gentle please. I'm on Lucid Lynx

Last night, the update manager installed updates to the linux kernel header. I'm not exactly sure what that means but it was one of the more important updates as it required a reboot. 

This morning, my machine would not boot. After getting past the loading screen, my laptop hangs on a black screen. It was working flawlessly before yesterday. 

I can boot into recovery mode which appears identical to the regular mode, which works fine and is what I've been using. Also, I used a custom bootscreen, but it seems to have reverted to the default one that comes with the Lucid Lynx install.

Remember, I'm a newbie.

---

### Post by Frogs Hair on 2010-06-06
Have you tried booting with the old kernel  ? In grub the latest kernel will be on top and then the previous . If it boots normally  with the old kernel and you are using a  proprietary graphics driver, remove the driver and try booting with the new kernel . If it boots reinstall the driver. If this is not the case I bump .

I had this issue with 9.10 and this worked for me.

---

### Post by dyslexicfurby on 2010-06-06
Thanks, I'll have to try that. How do I tell if I have a proprietary graphics driver, and how would I remove it?

---

### Post by dyslexicfurby on 2010-06-06
Update: I checked the hardware drivers utility. It says there are no proprietary drivers in use on my system.

---

### Post by Frogs Hair on 2010-06-07
I will bump to someone else, I thought it may be  same problem I had  . Does your computer boot normally with the old kernel ?

---

### Post by dyslexicfurby on 2010-06-07
Update: I have tried booting with an earlier kernel version and I get the same problem. However, I can boot to recovery mode fine. Still, this is annoying because I have to login and then type "startx" in order to get a desktop.

Any ideas?

---

### Post by dyslexicfurby on 2010-06-08
Are we allowed to bump threads? I'm still having this problem

---

### Post by yetiman64 on 2010-06-08
> **dyslexicfurby said:**
> Are we allowed to bump threads? I'm still having this problem

Yes, guidelines say it is ok to bump every 24 hours (though 19 hours seems not too bad -I've seen much worse here without comment ;)) Sorry can't help out further though re your actual problem.

---

### Post by dyslexicfurby on 2010-06-08
Got it: the new kernel update changed plymouth to use the default bootscreen Spincity or something like that. I changed it to another one (solar for those who care), and the system boots normally. It appears to be a problem with the boot skin itself, or maybe plymouth but everything is working now.

---

### Post by Tekmoor on 2010-06-08
Can you please describe how you did this fix? I'm having the same problem! Thanks

---

### Post by dyslexicfurby on 2010-06-08
I found this very helpful link to configure plymouth: [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

This is what I did. First I changed the default splash screen

```
sudo update-alternatives --config default.plymouth
```Select a splash screen; I chose 'solar' because it looks nice and works.

```
sudo update-initramfs -u
```I believe this cements your selection. I do not know if this next code is necessary or not but I did it as well. EDIT: the following code is a fix for the splash screen being very delayed

```
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
```I hope it works for you!

---

### Post by Tekmoor on 2010-06-08
Thanks for typing that out for me, unfortunately it didn't work. I can see the solar splash screen but after that I hear the login-screen-ready-sound and the screen just goes black. The login screen never appears and I can't get to the virtual consoles either.

EDIT: Okay I got it working by following Frogs Hair's advice! However, I had to boot into low graphics mode not an old kernel (that didn't work).

---

### Post by Gerald here on 2010-12-09
Thank you ! Changing the splash screen to Solar fixed my black screen hang problem.

---

