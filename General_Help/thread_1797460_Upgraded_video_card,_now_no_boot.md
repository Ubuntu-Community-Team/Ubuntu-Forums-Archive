---
title: "Upgraded video card, now no boot"
date: 2011-07-05
forum: General Help
---

### Post by Rich3077 on 2011-07-05
Upgraded to ATI 6950 video card. 
Okay so I dual boot Windows 7/Ubuntu 11.04? (not positive)
on separate hard drives.
When I booted into Ubuntu it booted just fine but was the wrong resolution. I read some how to's and copied and pasted into the terminal per the how to's. (no idea what I did really)

Now when I boot I get a black screen and it seems frozen, any of the commands I have found seemed to do nothing.
If I boot into recovery mode it loads about 4 lines of text and stops.

I have some important stuff backed up on my Ubuntu drive... and then my windows drive failed.. so I really need in there if possible. I have downloaded a new live CD because I think I may be able to fix the problem with that?? 

I am still pretty much a Linux newb so please be gentle!

---

### Post by mastablasta on 2011-07-05
uf, uf... throwing in commands without knowing what you are doing is a bad thing.
 
with live CD you should be able to access the hard disk. if you or a friend has external disk you could back up you data and then reinstall the OS.
 
resolution should be solved by either installing proprietary drivers or upgrading the opensource drivers. you should have tried that first.
 
also it's a bit hard to help if we don't know exactly what you did. :-)

---

### Post by Rich3077 on 2011-07-05
> **mastablasta said:**
> resolution should be solved by either installing proprietary drivers or upgrading the opensource drivers. you should have tried that first

Thats what I was doing, or at least trying to do by following How to's. I am pretty sure its just a video card issue... hope I don't need to reformat.

---

### Post by Rich3077 on 2011-07-05
Okay I find that if I hit e at the boot menu I have some options.
Also it says something about "Kernal Crash (insert gibberish here) Quite Splash"

---

### Post by wildmanne39 on 2011-07-05
> **Rich3077 said:**
> Okay I find that if I hit e at the boot menu I have some options.
Also it says something about "Kernal Crash (insert gibberish here) Quite Splash"Hi, see if the directions in this link can get you into ubuntu so you can change video drivers.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Rich3077 on 2011-07-05
Okay when I added nomodeset it seemed to do something because Ubuntu then did a hard drive scan.. then went to a splash screen.. but did not load.

I just found I was able to boot into an old kernal listed in the boot manager... I hope that helps for something.

Can I just upgrade this kernal and hope for the best?? Any other suggestions?

---

### Post by wildmanne39 on 2011-07-05
> **Rich3077 said:**
> Okay when I added nomodeset it seemed to do something because Ubuntu then did a hard drive scan.. then went to a splash screen.. but did not load.

I just found I was able to boot into an old kernal listed in the boot manager... I hope that helps for something.

Can I just upgrade this kernal and hope for the best?? Any other suggestions?Hi, you could but I would not until you know what the problem is, because I did that before and then I could not boot that kernel either because of of the same issue. I would go back to that page and try another option, or you said you think it was running disk check, have you tried to use that kernel since the disk check?

---

### Post by Rich3077 on 2011-07-05
Yeah I ran it again after a reboot and it just froze at the splash screen.
Its my bedtime so I will check this thread again tomorrow.

Thanks for your help!!

---

### Post by wildmanne39 on 2011-07-05
> **Rich3077 said:**
> Yeah I ran it again after a reboot and it just froze at the splash screen.
Its my bedtime so I will check this thread again tomorrow.

Thanks for your help!!
Hi, after you have tried the other options on that in link I gave you, if it still does not work, then try these two commands.
```
sudo rm /etc/X11/xorg.conf
```
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by linuxuser12345 on 2011-07-05
Try putting in the old video card, installing the new driver, then putting back in the new card?

---

### Post by Rich3077 on 2011-07-06
Working on this now. Was able to upgrade to the ATI proprietary drivers in the old kernal by uninstalling  fglrx from synaptic package manager and then just clicking on the ATI install package.

---

### Post by wildmanne39 on 2011-07-06
> **Rich3077 said:**
> Working on this now. Was able to upgrade to the ATI proprietary drivers in the old kernal by uninstalling  fglrx from synaptic package manager and then just clicking on the ATI install package.
Hi, let us know if you get it working and then mark the thread solved with instructions on how you did it so other people can benefit from your solution.

---

### Post by Rich3077 on 2011-07-06
Solved:  What I did was probably not the smartest way, but it worked for me.

I was able to boot into an old kernel. (that I was to lazy to remove)

Uninstalled fglrx using synaptic package manager. Installed ATI proprietary driver and then updated to Ubuntu 11.04 using the install CD. 

This was the best option for me because I had several problems with my Ubuntu install due to trying to customize the kernel to make sound work in Quake 3 Arena.  

Thanks everyone for your help.

---

### Post by wildmanne39 on 2011-07-06
> **Rich3077 said:**
> Solved:  What I did was probably not the smartest way, but it worked for me.

I was able to boot into an old kernel. (that I was to lazy to remove)

Uninstalled fglrx using synaptic package manager. Installed ATI proprietary driver and then updated to Ubuntu 11.04 using the install CD. 

This was the best option for me because I had several problems with my Ubuntu install due to trying to customize the kernel to make sound work in Quake 3 Arena.  

Thanks everyone for your help.Hi, thats great I am glad you got it working and sometimes it is best to do it that way if you have tweaked a lot of settings.

---

