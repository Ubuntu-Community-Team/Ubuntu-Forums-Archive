---
title: "Nvidia Drivers not working at all."
date: 2009-09-12
forum: General Help
---

### Post by grungerokker13 on 2009-09-12
Ok I've done a lot of digging and it looks like this is a very common problem but most of the proposed solutions haven't worked for me.

I'm running Ubuntu 9.04.  I just did updates and then went to enable restricted drivers.  I've tried both the 180 and the 173.  Both have similar results:

Most of the time I'll only get a cli and no gui what-so-ever.  It says that gnome is running and when I stop it (/etc/init.d/gmd start/stop/restart) and start it again....nothing changes except the screen blinks a couple of times.  

Sometimes it will just go through the loading prompts and after: "checking battery state" it just stops and the only thing I can do is ctl+alt+delete to reboot the machine and even then it says "stopping gnome display manager" even though there's no gui.

And sometimes my monitor will just go blank.

I have NO IDEA what to do now.  I've had to reinstall ubuntu about 7 times and I've tried  both sets of restricted drivers....both get similar results.  If I get lucky enough to get into the command prompt, I can remove the driver and the machine boots back into gnome just fine....All I need the drivers for is random compiz stuff.


My machine:
Q6700 quad 2.66
evga 780i mb
4 gb ocz memory
I am also running 2 Nvidia 9800gtx+ video cards.  I was wondering if just having them sli'd together would cause this issue but I don't believe it would.  I don't care if the SLI doesn't work, I only need it to recognize one card.  All of the hardware works fine with windows just an FYI.

Please help any way that you can.  I can provide any information about the system that you need.

---

### Post by synapsys on 2009-09-13
Have you tried downloading from nvidia's website?

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by grungerokker13 on 2009-09-13
Yes with the same result.

---

### Post by 3rdalbum on 2009-09-13
I think the 173 drivers are too old for you to run any 9800s.

Take out the SLI bridge and see if that works, with the 180 drivers. Otherwise, the latest Nvidia driver version is 185 (must be manually installed), so you could try that.

---

### Post by DeMus on 2009-09-13
> **3rdalbum said:**
> I think the 173 drivers are too old for you to run any 9800s.

Take out the SLI bridge and see if that works, with the 180 drivers. Otherwise, the latest Nvidia driver version is 185 (must be manually installed), so you could try that.

Sorry, the latest version is 190.25, see attached picture.


Oops, I just saw it is 190.32 already.

---

### Post by fanglinyong on 2009-09-13
when you want to install the your graphic software ,you must do like what i said.yes, the ```
 /etc/init.d/gdm stop 
``` is right, the problem is the sort!
must do like this:
```

first ,you ust exce the code by this way :
1.applications--->accesories--->terminal
2.type[code] /etc/init.d/gdm stop 
```
3.then, you may see that, you have go into textmode,and ,you can install your nvidia drive software!
[/code]
good luck!!!
remmember:you must exce the code in your x-server mode!

---

### Post by grungerokker13 on 2009-09-13
I have tried all of that, and I can't take out my sli bridge because I run windows nativly and will be virualizing ubuntu.  At the moment though I have been testing witha fresh install of ubuntu on a seperate partition so it has nothing to do with virtualizing it.    I'd have to replace my sli bridge everytime I wanted to log into windows and play a game.


Any other suggestions, everything suggested so far I've tried. :(

---

### Post by markiep on 2009-09-20
I am using 9.04 and also have this problem, no matter what i do i cannot get the drivers to load i have a 680i motherboard dual 8800gtx vid cards 2 gig of ram i have tried on and off for two and a half months. i tried taking card out, installing driver from nvidia. yadda yadda yadda. 
    I tried karmic to see if maybe there was something different, i had to switch my monitor to CRT for karmic to work, seems it doesn't like my 22" acer flat screen and won't boot to live cd. still no fix for nvidia with my setup. i would use 1 card also if i could get it to work but seeing i have XP on another drive i just keep using it untill maybe just maybe there will be a fix.
    I wish i could find a straight answer for why this is happening, i also understand the problems associated with nvidia drivers, but somewhere something went wrong it used to work with 8.04 untill i updated something and no more video in 8.04, what that something was? got me. So if anyone knows a solution or an answer to these problems i would love to hear from you.

---

