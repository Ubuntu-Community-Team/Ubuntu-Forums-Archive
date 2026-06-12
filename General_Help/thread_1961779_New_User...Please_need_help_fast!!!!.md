---
title: "New User...Please need help fast!!!!"
date: 2012-04-19
forum: General Help
---

### Post by clk55r1d3h on 2012-04-19
Ok, as you can see i'm new to linux. I decided to install ubuntu 11.10 over my windows 7 (don't have anything important on it), so everything went smooth I logged in and downloaded ati 12.3 drivers from the website, installed it fine. Then it told me I had 300 something new updates so I went ahead with the update. 
        After everything was done it told me to restart. After clicking restart it goes to the ubuntu screen with 5 purple dots and just gets stuck, I can not press anything, I tried everything but nothing works so I had to manually shut the computer down and now I can't get past ubuntu screen, like I said nothing works I can't get the log or anything. 
       Right now i'm in the process of reinstalling ubuntu again, but I need to know what the problem is, could it be the updates itself or maybe the ati drivers. Any help would be appreciated, thank you.

BTW i'm very illiterate when it comes to linux....

---

### Post by sffvba[e0rt on 2012-04-19
I would suggest installing the drivers that come with Ubuntu 11.10.  Simply look for "Additional Drivers" and then select the drivers from there.  Do this after installing all updates.

If after this you are still having issues like you describe you can hold the shift key when booting to get the grub menu.  Then add *nomodeset* to your boot options. (Some help with that here [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132))

Once you have done that you should be able to get into the system then it is possible to continue troubleshooting.


404

---

### Post by clk55r1d3h on 2012-04-19
> **not found said:**
> I would suggest installing the drivers that come with Ubuntu 11.10.  Simply look for "Additional Drivers" and then select the drivers from there.  Do this after installing all updates.

If after this you are still having issues like you describe you can hold the shift key when booting to get the grub menu.  Then add *nomodeset* to your boot options. (Some help with that here [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132))

Once you have done that you should be able to get into the system then it is possible to continue troubleshooting.


404

Thanks for the fast response...I just finished the installation and without updating anything I clicked on restart, now this time it just got stuck at a black screen, I had to push my power button again which brought up the ubuntu logo with the dots and just turned off.
So I started the computer again and now it gives me some numbers and says "Reset Adapter" I don't know what is going on this is fresh install that I just did right now.

---

### Post by sffvba[e0rt on 2012-04-19
> **clk55r1d3h said:**
> Thanks for the fast response...I just finished the installation and without updating anything I clicked on restart, now this time it just got stuck at a black screen, I had to push my power button again which brought up the ubuntu logo with the dots and just turned off.
So I started the computer again and now it gives me some numbers and says "Reset Adapter" I don't know what is going on this is fresh install that I just did right now.

Hmmm... that is odd...

I don't think this is something that will be fixed quickly so I suggest some patience and letting some of the guru's show up and together you will fix this. (As a side note, you could try the nomodeset suggestion of mine and see if it works).


404

---

### Post by clk55r1d3h on 2012-04-19
> **not found said:**
> Hmmm... that is odd...

I don't think this is something that will be fixed quickly so I suggest some patience and letting some of the guru's show up and together you will fix this. (As a side note, you could try the nomodeset suggestion of mine and see if it works).


404

Thanks a lot, I'm going to try to do that...right now when I pressed alt+ctr+del it restarted but its the same thing now...so I will try nomodeset right now...thanks again...

---

### Post by jadtech on 2012-04-19
never do a cold shut down  that is most likly  the issue this time no matter how tempting the off button seems :)

---

### Post by clk55r1d3h on 2012-04-19
> **jadtech said:**
> never do a cold shut down  that is most likly  the issue this time no matter how tempting the off button seems :)

Haha ok my bad...

---

### Post by clk55r1d3h on 2012-04-19
Ok I did the nomdeset thingy and I got into the system I'm doing all my updates now and I'm going to give it a try, I'm just scared that it might get stuck like before where I couldn't do anything at all...

---

### Post by Bucky Ball on 2012-04-19
Does it work ok when you 'Try Ubuntu' from the LiveCD?

When you install, at the bottom of the first screen where you get options to install or try, press F6 and use the 'nomodset' option as suggested, then install. See if that makes a difference. 

To try this now (before installing again - try and avoid that), when you boot the machine hit shift and that should take you to the grub menu. Choose the kernel you want to boot then 'e' to edit it.

Find the line that ends 'quiet splash' and add 'nomodset', save and continue with boot (instructions to do that at the bottom of the screen).

Good luck.

---

### Post by sffvba[e0rt on 2012-04-19
> **clk55r1d3h said:**
> Ok I did the nomdeset thingy and I got into the system I'm doing all my updates now and I'm going to give it a try, I'm just scared that it might get stuck like before where I couldn't do anything at all...

Well AFAIK if nomodeset works it is a graphics related issue... remember after installing the graphics drivers to run *sudo aticonfig --initial* in a terminal before restarting (forgot to mention that earlier).


404

---

### Post by clk55r1d3h on 2012-04-19
> **not found said:**
> Well AFAIK if nomodeset works it is a graphics related issue... remember after installing the graphics drivers to run *sudo aticonfig --initial* in a terminal before restarting (forgot to mention that earlier).


404

Ok sounds good I'm going to install the graphics driver now before restarting and do what you said...thanks for your help...oh and one more thing mine doesn't end with "quiet splash" there is something else after also can't remember what it was, but I inserted nomodeset after everything not "quiet splash"

---

### Post by sffvba[e0rt on 2012-04-19
> **clk55r1d3h said:**
> Ok sounds good I'm going to install the graphics driver now before restarting and do what you said...thanks for your help...oh and one more thing mine doesn't end with "quiet splash" there is something else after also can't remember what it was, **but I inserted nomodeset after everything not "quiet splash"**

That is fine... it will vary from system to system...


404

---

### Post by clk55r1d3h on 2012-04-19
> **not found said:**
> That is fine... it will vary from system to system...


404

Got it thanks, hopefully after all this it works...So, from what I understand the nomodeset resets after I boot up, does that mean I need to make it permanent or will running aticonfig fix that issue...

---

### Post by sffvba[e0rt on 2012-04-19
> **clk55r1d3h said:**
> Got it thanks, hopefully after all this it works...So, from what I understand the nomodeset resets after I boot up, does that mean I need to make it permanent or will running aticonfig fix that issue...

AFAIK using nomodeset is a workaround and not normally used permanently.  (I know when I normally used it I didn't have all of the functionality from my system graphically).

But if it works when you set it and doesn't when you don't at least we know where to start focusing further troubleshooting efforts :)


404

PS - I am off now to go home and sleep... all the best getting it working, and I am sure the answers you seek are here somewhere :)

---

### Post by clk55r1d3h on 2012-04-19
> **not found said:**
> AFAIK using nomodeset is a workaround and not normally used permanently.  (I know when I normally used it I didn't have all of the functionality from my system graphically).

But if it works when you set it and doesn't when you don't at least we know where to start focusing further troubleshooting efforts :)


404

PS - I am off now to go home and sleep... all the best getting it working, and I am sure the answers you seek are here somewhere :)

Ok thanks a lot for your help, I think it worked I just restarted after everything and it booted up fine.

---

