---
title: "Ubuntu 11.04 won't boot after improper Shutdown"
date: 2011-09-29
forum: General Help
---

### Post by javacookies on 2011-09-29
i just installed Ubuntu 11.04 on my old laptop. Everything was working well even compiz,which what I really want to see. All is well until the laptop got hot and everything is lagging until it just stops and hangs. No other way to restart but to hold the power button until it shuts down.After that, I can't boot to ubuntu,only XP. It just continue to the flashing cursor then it goes black screen. Even I wait long nothing happens. I even tried booting to recovery console but even that won't work. Anyone can help me? Thanks you very much :)

---

### Post by LinuxFan999 on 2011-09-29
Which file system did you use when installing Ubuntu?

---

### Post by javacookies on 2011-09-29
i think ext4...'coz that's the default?
BTW,I installed it through wubi. Even booting to recovery mode,it goes to blank screen after the flashing cursor :(

---

### Post by bcbc on 2011-09-29
It sounds like you need to fsck the root.disk: [https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F)
Ignore the bit about mounting the root.disk, and just run the fsck. 

In the future, you can use Alt+SysRq R-E-I-S-U-B to reboot when it's hanging. Hard shutdowns can be fatal to Wubi installs.

---

### Post by javacookies on 2011-09-30
how can i run fcsk? I can't go to recovery mode......
thanks for the replies :)

EDIT:now I'm stuck to the flashing cursor...can't even get past to it

---

### Post by bcbc on 2011-09-30
you need to boot a live CD/USB - i.e. download the ubuntu desktop cd image, burn it to CD or create a bootable usb, and boot it.

Instructions to create a CD/USB are here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by javacookies on 2011-09-30
after that what should I do?.....i tried chkdsk /r from windows...after that I managed to reach login screen but the mouse lags and it suddenly turned off. This is what happened the moments before this problem occurred.

---

### Post by bcbc on 2011-09-30
What's the brand/model/graphics card?

PS the instructions for fsck'ing the root.disk were in that link I gave to the wubi guide. If you need more help, then post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") (also run from live CD).

---

### Post by javacookies on 2011-09-30
looks like my laptop doesn't support booting from USB and I don't have access to any blank CD. BTW, it's Acer Travel mate 2420(Mobile Intel 915gm/gms
I'm suspecting it's a hardware problem....because this one's old although I'm booting XP fine.

EDIT: I didn't do anything....now it booted...I don't really understand.Hope it won;t happen again. Thanks for all the help. I'll be back here if ever it will happen again.Thanks again :)

---

### Post by bcbc on 2011-09-30
hmm there are a bunch of hits on that model, but  not much in the way of fixes. There is one at the end of this bug report which I traced via duplicate bugs so it may not seem relevant.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/477256?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/477256?comments=all)

Here's the first thread I found on this: [http://ubuntuforums.org/showthread.php?t=1744830](http://ubuntuforums.org/showthread.php?t=1744830) 

Maybe someone on that thread has found a resolution - worth posting I suppose.

Good luck!

---

### Post by javacookies on 2011-10-16
I'm experiencing it again, Not just on 11.04 but also in 10.10. This starts happening when the system hangs. I don't know why it hangs but using alt + sysrq+REISUB won't work so I have no choice but to push the power button until it's off. After that, it won't boot even recovery console.In normal boot,it will usually go after the blinking cursor and the screen goes black. In recovery console, it will only go until there are texts displayed like filesystem mounted blah blah. I'm just starting to love Ubuntu but these problems really stops me to fully love the OS.

---

### Post by javacookies on 2011-10-16
looks like a problem with my onboard video card? I just installed 11.10 it's not booting too,not even once.....hmmm.I wonder what's the real problem. I want Ubuntu. Please help me :D

PS:I installed 10.10 and 11.10 on dedicated partition while 11.04 through wubi. XP is booting perfectly.

---

### Post by javacookies on 2011-10-17
Got 11.04 booted, but it was a pain. I've waited for about 30 mins and when i finally got into the login screen. the mouse and keyboard stop responding every 5-10 secs. With that, I still managed to login for about 5 mins, with login sound lagging and the desktop slowly appearing. Then I thought everything was okay because screensaver compiz plugin activated but when I canceled it it lagged again....and boom it hanged again. please someone help me, I want to use Ubuntu but it seems like very unstable to me :(

---

### Post by bcbc on 2011-10-17
Try a couple of boot options: 
i915.modeset=0 
or 
i915.modeset=1

or
Try this: [https://launchpad.net/~ubuntu-x-swat/+archive/ppa](https://launchpad.net/~ubuntu-x-swat/+archive/ppa)

Post your /var/log/syslog

I don't have any bright ideas, but since you're not getting any other responses... might as well try a few things ;)

---

### Post by javacookies on 2011-10-17
thanks I'll try those. I wonder what's causing this. I can't even boot from Live CD from USB.I've even tried other HDD and installed other ubuntu but still no luck. Only windows boot properly. Does my laptop reject Ubuntu? LOL

---

### Post by javacookies on 2011-10-17
i915.modeset didn't work :( and i can't try this [https://launchpad.net/~ubuntu-x-swat/+archive/ppa](https://launchpad.net/~ubuntu-x-swat/+archive/ppa) coz i can't go to any terminal from recovery mode or from live cd. Both won't boot. And how can I see my var/log/syslog if i can't go to any terminal? sorry for being a noob :)

---

### Post by bcbc on 2011-10-17
> **javacookies said:**
> i915.modeset didn't work :( and i can't try this [https://launchpad.net/~ubuntu-x-swat/+archive/ppa](https://launchpad.net/~ubuntu-x-swat/+archive/ppa) coz i can't go to any terminal from recovery mode or from live cd. Both won't boot. And how can I see my var/log/syslog if i can't go to any terminal? sorry for being a noob :)

Yeah that makes sense - if you can't boot you can't try those things...

So there's no reason why your computer can't boot from USB or CD. Generally some computers are set to 'express boot' and might not allow override at boot time (in which case you need to enter the BIOS and disable this), but if it is clearly booting from the USB/CD and failing then it indicates a bad burn on the CD or a mistake setting up the USB. The [ubuntu download site]("http://ubuntu.com/download/ubuntu/download") contains instructions on how to create these (step 2, show me how).

If you had 10.04 running before, it should run fine again. And you can at least use the USB to try out other versions to make sure they run on your hardware before installing.

---

### Post by javacookies on 2011-10-18
That's what I'm trying to say. I'm sure I made the pendrive properly. It's booting because I see the menu like install ubuntu or boot from usb. But when I try to boot from USB, it hangs on black screen and turns off after couple of minutes.I have 11.04 in one hdd and 10.10 on the other. Both isn't booting and I decided to overwrite 10.10 with 11.10. It was installed okay though installing it was a pain since it's lagging too....but the sad part is it's not booting too. so sad...I got two weird problems on Ubuntu...one on my desktop one my laptop.:(

---

### Post by bcbc on 2011-10-18
Refer to this: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Change the boot options on the live USB (F6) and remove the 'quiet splash'. See where it freezes - maybe will indicate the problem and make searching for a solution easier.

You could also try a few other options - noacpi etc.

Make sure your computer bios is up to date as well.

---

### Post by javacookies on 2011-10-19
Tnx again for the reply
I've tried removing quiet splash. The system hangs on Begin: Running /scripts/init-bottom and that applies n both the normal and recovery mode. I can't use ctrl alt delete there or even alt sysrq REISUB

EDIT: Every ubuntu I tried to boot,both normal and recovery mode lnow leads to a blank screen.It doesn't even output something on my external monitor. I also tried installing fedora but even that won't boot. Could this be BIOS related? I have the latest but I'm thinking of reflashing it

---

### Post by bcbc on 2011-10-19
> **javacookies said:**
> Tnx again for the reply
I've tried removing quiet splash. The system hangs on Begin: Running /scripts/init-bottom and that applies n both the normal and recovery mode. I can't use ctrl alt delete there or even alt sysrq REISUB

EDIT: Every ubuntu I tried to boot,both normal and recovery mode lnow leads to a blank screen.It doesn't even output something on my external monitor. I also tried installing fedora but even that won't boot. Could this be BIOS related? I have the latest but I'm thinking of reflashing it
Does you laptop monitor not work? It's best to trouble shoot without plugging in an external monitor. It's not likely a bios issue.

---

### Post by javacookies on 2011-10-19
no it's not broken. I just tried it if it somehow solve something. I tried that first last day and I don't know if that's the reason why i booted after almost 30 mins and able to login but still lags and finally hanga at the end :(

---

### Post by javacookies on 2011-10-21
is it possible that it could be related to my wireless network? Whenever I turn on my wireless lan on XP, my laptop hangs. Do you think blacklisting the module for it in ubuntu could fix my problem?

---

### Post by bcbc on 2011-10-22
> **javacookies said:**
> is it possible that it could be related to my wireless network? Whenever I turn on my wireless lan on XP, my laptop hangs. Do you think blacklisting the module for it in ubuntu could fix my problem?

I would get a list of your hardware and look for published issues/workarounds. It's hard to speculate not knowing the specifics. Also, it's a good idea to post in the relevant forum e.g. networking and wireless as the people who monitor it tend to focus on these issues.

Something I am curious about - when 10.04 was working on your laptop, was the screen still working or did you have the external monitor in place? 
If you've tried 10.04 again and it doesn't work now, then likely some hardware has failed - it seems a logical conclusion.

---

### Post by javacookies on 2011-10-23
Actually everything was working well on my laptop. 10.04,10.10 and 11.04. I can install them through booting from USB or wubi. But now, nothing's working. My logical speculation is since opening my wireless on XP hangs the system. It could also be the cause of my problem in Linux. If i'm not mistaken, whenever ubuntu boots, wireless module also boots and also maybe the same thing happens when Ubuntu or Fedora is booted from USB. So maybe that causes ita nd blacklisting it could solve it.

BTW, i don't really use the external monitor.Actually it's our television and I just tried it hoping it could fix the black screen of death :) Anyway, thanks again,I'll try posting in Networking and wireless ;)

---

### Post by javacookies on 2011-10-24
I  noticed 11.10 is can be booted in recovery mode. I saw in it use nomodeset so i tried it in 11.04 recovery mode. It booted in failsafe mode, then I tried in normal boot and it booted too! :) I still don't know what makes it work now although I don't know if this will be like this for a long time coz the problem might reappear again. Anyway,thanks for all the help. Like on all topics here, I'll be back when the problem strikes again ;)

EDIT: nevermind my stupid post above. I just confirmed it, my wireless lan is the culprit! I thought i was blacklisting it the right way but i echoed 'blacklist ipw2200' in blacklist not blacklist.conf. SO when I tried id it the right way, it then booted without any problem and without waiting for 30 mins :D Now I wonder if i can use blacklisting in booting from USB coz I want to install 11.10. And also looks like blacklisting my wireless lan caused the date,network manager,shutdown,etc on my panel nowhere to be found, just blanks and separators.

---

