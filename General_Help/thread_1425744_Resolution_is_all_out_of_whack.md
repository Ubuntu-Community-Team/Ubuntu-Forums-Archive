---
title: "Resolution is all out of whack"
date: 2010-03-09
forum: General Help
---

### Post by Apexi38 on 2010-03-09
alright, so at work one day I had set up my Asus eee 1000he to another moniter and set up dual monitors.  I shut down, and here is where I think the problem lies, I didn't change it back to single monitor before I shut down.  Now when i boot up the machine, it loads just fine through bios and the Ubuntu splash screen but when its supposed to hit the desktop, I get about an inch or two if static like kines across my screen and one small line that runs the entire way across that i can control with my touch pad. the monitor I hooked it up to was set to 1920x1080.  I may be wrong but, I'm thinking Ubuntu is trying to cram all that information on to the eee's screen and it can't handle it.  If anyone knows how to fix this it would be greatly appreciated!

---

### Post by patchwork on 2010-03-09
Try hitting CTRL+Alt+(+) <plus sign> and CTRL ALT - (minus sign)

This should toggle you through the available resolution settings, if you still have multiple valid settings.

---

### Post by Apexi38 on 2010-03-09
Yea I already tried that, it seems to open a window but I can't tell what that window is.

---

### Post by patchwork on 2010-03-09
What is listed with xrandr?

```
xrandr
```

---

### Post by Apexi38 on 2010-03-09
it says "Can't open display"  Not to sure what that means

---

### Post by patchwork on 2010-03-09
How bad is the screen?  Can you use it to view things in the terminal or a text editor?  If not, drop to console using CTRL ALT F1 to execute the following commands.

If you can see the text editor cleanly, feel free to use it to view these files.

Alternately, if you can paste the results here, I'd like to take a look at them. 

```
cat /var/log/Xorg.0.log | more
```
This will allow you to view your x server log.  Look for anything indicating a fatal X server error (and the reason, if given), also look to see what modes are being validated (and which ones are being rejected).

```
sudo nano /etc/X11/xorg.conf
```
Check to see how many monitor sections are listed, and check to see if one of them conforms to the netbook monitor.

---

### Post by Apexi38 on 2010-03-09
well unfortunately I cannot copy paste, my screen really just looks like about an inch of static across the center.  I did just run the log and one thing that popped up right at the end was 
(WW) Warning couldn't open module nvidia
(II) unload module "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers avalible.

Fatal server error:
no screens found

---

### Post by patchwork on 2010-03-09
Reinstall the nvidia video drivers, restart x, and see if that helps.

---

### Post by Apexi38 on 2010-03-09
nope, didn't help.  I'm thinking something must have just went FUBAR not really sure where.  Im probably just going to reinstall ubuntu at this point.  Ive been attempting to fix this problem for about a week now

---

### Post by patchwork on 2010-03-09
Is nvidia listed in lsmod?

```
lsmod | grep nvidia
```

If not, can you hotplug the module in?

```
sudo modprobe nvidia
``` and restart X?

---

### Post by Apexi38 on 2010-03-09
when i run lsmod i don't see it anywhere.  Mind you I'm forced to be doing all this in repair prompt so it may be near the top.  when I run modprobe it gives me a fatal error that there is no such device.

---

### Post by patchwork on 2010-03-09
I'm looking at the specs for the Asus eee 1000he and I don't see a Nvidia graphics processor anywhere....am I wrong?


I see Intel 945

Why is your x server trying to load the nvidia module?  What is the content of your /etc/X11/xorg.conf?

---

### Post by Apexi38 on 2010-03-09
well yea, I see that now too.  Well that's the issue..... Now I have installed the Intel Drivers and the same issue is occurring, it looks like the resolution of 19XX x 1024 is still sticking.

---

### Post by patchwork on 2010-03-09
Have you restarted the x server? 
If so, have you checked the /var/log/Xorg.0.log again?  
 
Have you double checked your /etc/X11/xorg.conf to make sure nvidia isn't listed as the driver in the "Device" section? 

Have you tried xrandr or CTRL ALT + or - since swapping drivers?

---

### Post by patchwork on 2010-03-09
Did the resolution work "out-of-the-box"?  If so, it may be easier to move your xorg.conf to a back-up location, and let the system create it's own configuration:

```
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

And restart X

---

