---
title: "Ubuntu 12.04 has experienced an internal error"
date: 2012-04-28
forum: General Help
---

### Post by nizamibilal1064 on 2012-04-28
Hi 
I had upgraded to ubuntu 12.04 1 day ago. It was working fine. today while browsing net a window just pop up with error massage "ubuntu 12.04 has experienced an internal error". It seems that genome has crashed  Does any body has any idea???:confused:

---

### Post by iponeverything on 2012-04-28
next time, click the "details" button -- so that you can provide more specific information..

this type of problem is not uncommon in initial wide releases..

---

### Post by johnnyhajjar on 2012-04-28
I'm experiencing an error as well. I recently upgraded from 11.10 and something clearly went wrong. There are no controls in gnome, and I keep getting a message saying that there is an internal error.

---

### Post by miii123 on 2012-04-28
I'e had this error also, but after that, nothing happened, just used the computer without a problem.

---

### Post by coldjeanz on 2012-04-28
Same. I clicked details but not being that familiar with Ubuntu I couldn't really figure out the problem. I just ignored it since everything seems to be fine.

The "send error report" thing is bugging me though. I don't want that Windows non sense on my Linux system, I thought that was one of the main perks of Linux. :confused:

---

### Post by chapulin on 2012-04-28
Same here!... I'm not sure if this about that bug, but I saw a a landscape fail when my computer shut down.

---

### Post by chapulin on 2012-04-28
Also I can't save an software icon in the left toolbar... When I turn on my computer, the left toolbar doesnt save my icons.

---

### Post by iponeverything on 2012-04-29
This "error" is not same on every system - for folks to jump in with a "I get this too" type of responses -- does not help. There is a "details" button associated with the dialogue box associated with the message - it will provide information on the cause that triggered of bug reporting subsystem.

---

### Post by iponeverything on 2012-04-29
> **coldjeanz said:**
> Same. I clicked details but not being that familiar with Ubuntu I couldn't really figure out the problem. I just ignored it since everything seems to be fine.

The "send error report" thing is bugging me though. I don't want that Windows non sense on my Linux system, I thought that was one of the main perks of Linux. :confused:

Ubuntu is is just a flavour of Linux -- some flavours are less buggy than others - Ubuntu is bleeding edge as far as distributions go - 

It is not clear to me what you mean by "Windows non sense"? Are you talking about buggy software, intrusive behaviour, or something else?

---

### Post by nizamibilal1064 on 2012-05-02
It was having problem with screenlet application. i Uninstalled it, after this problem reduces but still it shows some problem with gnome. some time it says gnome crashes or intel.py having problem. I will give the screen shot next time.

---

### Post by rbaleksandar on 2012-05-03
Hi, guys!

  Well, I upgraded last night from 10.04 LTS to 12.04 LTS. I got a couple of minor errors during the installation but it was nothing special. On my first login in 12.04 I got a greeting that "Ubuntu [SIZE="4"]10.04[/SIZE] has experienced an internal error" (although I was already with 12.04 :confused:). This morning I got the same error but with the correct version number this time. It says that the problem is in **blueman-applet** (blueman-applet crashed with the DBusException in call_block()), which I set to be loaded on startup (Bluetooth is needed here :P).
  But that's not a problem at all compared to the other thing that I'm experiencing right now - I have no Unity. No panels, no hotkeys that are connected to the Unity-interface (like Alt+Tab for Window-switching, like Alt+F1 for the Unity-Home (or whatever the uppermost icon with the Ubuntu-logo is called). I have no clock, no user-menu, no indication area - N-O-T-H-I-N-G. Good thing that I can use the terminal more or less. :lolflag: Another thing that might be curious for you:

[LIST]
[*]After installing Ubuntu 12.04 I uninstalled the Cairo-Dock (not the libs etc., which are needed by other programs). After I got this peculiar behaviour, I reinstalled it (I installed it back then with Ubuntu 10.04 but never used it so...) but this didn't change anything.
[*]The Psendos-indicator (for temperatures monitoring) is loaded (:confused:) but since there are no panels, it's loaded in a separate window (:confused::confused:) like a normal program.
[/LIST]

I also have to mention that I have Compiz installed but in 10.04 it was just with the productive features enabled (nothing like rainy/flamy desktop, cubes, transperancy etc.).

If you need any other information, I'll gladly post it here. Please help! I have upgraded only three times (first time was with Ubuntu 5.10 to 6.04 LTS) and it always went wrong for some unknown reason(s). Ever since I did fresh installs but this time I just spent like 2 years with Ubuntu 10.04 LTS (ever since it came out I have reinstalled it only two times (the first time: change of the machine; the second time: corrupted HDD file system caused by GParted's crash -> complete wipe-out of the whole HDD)), so it kind of grew on me and I started making minor tweaks etc., which I didn't want to loose and it was too much of a pain in the bum to back all these things up.

Thanks a lot!

PS: Right now I'm reading this article: [http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
So I hope it helps.


EDIT: Ok, it's working. Did all that was described in the link above. After I uninstalled the FGLRX, I got some flickering when I tried to restart the GDM. So I had to make a cold restart (pushed the almighty plastic button). And there you go - I have Unity again. So now I'll try to reinstall the drivers. If I get the same problem, I'll have to live without them for a while. The problem might have been in the Xorg.config, which I backed up and a new one was created.

---

### Post by dove-young on 2012-05-03
I experienced internal system error almost every day.  

I used Thinkpad T400. It worked very smoothly since Ubuntu 10.04. My Ubuntu 12.04 is fresh installed. So it is very ugly so far.

---

### Post by saneearth on 2012-05-03
There are still several glitches for which you might receive errors. Unless you click the details button, you will not know what it is and it could be anything. I too am having some odd behaviour and crashes with screenlets, though I keep running it. I have also had some issues with Docky. One other odd issue that seems to possibly have gotten better is that when using "save" in nautilus or other programs mouse clicking will not expand a folder and I find I have to click on the folder and then hit the enter key to expand the folder. Anyway, most everything is working great for my now, but there are still some minor bugs.

---

### Post by DenysT on 2012-05-03
I get this message on the 32-bit desktop and laptop for the weather indicator applet...disable/uninstall the applet until it gets fixed I guess. But the Opera browser does the same thing on both the 32 and 64-bit desktops (some built-in plugin so probably Opera's fault). Who to report it to, Opera or Canonical?

---

### Post by Dennis N on 2012-05-04
Just Apport doing its job. It generates crash reports for debugging purposes. 

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

From reading this, and looking at the relevant file, it can be disabled if desired by setting enabled=0 in /etc/default/apport

---

### Post by brad1138 on 2012-05-04
Same here, get it all the time, sometimes 3 or 4 per boot. A lot of them were related to screenlets, other "colord" (whatever that is), others I don't remember. I got tired of them and started click "don't show again" system always seems to work fine.

---

### Post by buckeyered80 on 2012-05-05
Dennis N seems to have the best solution for me. I am not having any actual issues, so I just disabled the Apport. My system is working fine after upgrade, but that error message was a bit annoying. Thanks for sharing the location of that file.

---

### Post by twipley on 2012-05-06
Same here. Everything apparently working correctly, except such kinds of error messages popping up now and then. Fresh install on two computers, and the only installed thing are one proprietary driver on each, and the restricted extras on both.

The error-reporting system routine can be disabled through running:

```
sudo nano /etc/default/apport
```

and then changing the value of the "enabled" parameter from "1" to "0," taking care to exit through "CTRL-X," and then "y."

---

### Post by bogan on 2012-05-06
Hi!, **All.**

I had dozens of  "xxx /12.04 has experienced an internal error", "System Program Problem Detected" or "xxx/12.04 has stopped unexpectedly" messages during the first four days of running it, after an Update Manager upgrade from 11.10. 

Mostly they were unity crashes but only two caused actual crashes needing a reboot. Virtually all produced a note to the effect that it was a duplicate of bug report No.xxxxxx.

Finally, I ran ```
sudo dpkg-reconfigure -a 
```and since then I have - in five days - only had one such message, and that was directly after running 'unity-reset', which hung after producing dozens of WARNINGs.

There was a message that it would take a long time but, in fact, it only took about 20 minutes.

Chao!, **bogan.**

---

### Post by iranai on 2012-05-06
> **bogan said:**
> Hi!, **All.**

I had dozens of  "xxx /12.04 has experienced an internal error", "System Program Problem Detected" or "xxx/12.04 has stopped unexpectedly" messages during the first four days of running it, after an Update Manager upgrade from 11.10. 

Mostly they were unity crashes but only two caused actual crashes needing a reboot. Virtually all produced a note to the effect that it was a duplicate of bug report No.xxxxxx.

Finally, I ran ```
sudo dpkg-reconfigure -a 
```and since then I have - in five days - only had one such message, and that was directly after running 'unity-rese', which hung after producing dozens of WARNINGs.

There was a message that it would take a long time but, in fact, it only took about 20 minutes.

Chao!, **bogan.**


I'm trying this now.  11.10 worked fine with Unity 3D. If I log into regular Ubuntu, Unity does not work (no sidebar or  titlebar menus etc.). Thus, I have to select the gear on the login page  and use Unity 2D.  

It seems that many of the issues I have revolve around ATI drivers.  I have tried both new proprietary drivers and non open-source.  

What is strange is that in terminal "/usr/lib/nux/unity_support_test -p" shows opengl fully working and "glxgears" works fine, but when watching videos, I can no longer use the opengl drivers...and of course no Unity 3D... I want my cube back [-o<

Edit: running the above code brings back error:
** (accounts-daemon:26078): WARNING **: Failed to acquire org.freedesktop.Accounts
** (accounts-daemon:26078): WARNING **: Could not acquire name

I don't have time to trouble shoot that now, will need to come back to it.

---

### Post by Myoldmopar on 2012-05-09
Odd:

Bogan typed:  

"... rectly after running '*unity-reset*', which hung af .. "

Yet in Iranai's quote it came out as '*unity-rese*'

Random...good luck with your problems.  I arrived on this page because I am also seeing some miscellaneous system problems after upgrading from 11.10 to 12.04.

---

### Post by Joshun on 2012-05-09
If any of you haven't tested 12.04 with the livecd (but just upgraded), it would be worth downloading it and testing it to see whether it is a reproduceable bug or some problem during upgrade. Binary drivers (ATI, NVIDIA etc.) are known for problems when upgrading. If the problem is not with the graphics drivers but just with compiz/unity crashing, you could try resetting its config if you haven't already:

[http://askubuntu.com/questions/70866/how-to-reset-compiz-unity-to-defaults]("http://askubuntu.com/questions/70866/how-to-reset-compiz-unity-to-defaults")

With NVIDIA drivers, you may have to run ```
nvidia-xconfig
``` to get the driver working again.

If you are experiencing any flickering with either cards, check /etc/X11/xorg.conf (if it exists), and make sure the resolution and refresh rate are set to something sensible.

Joshun

---

### Post by rulet on 2012-05-10
It's not driver related bug. Just turn off apport.

---

### Post by nizamibilal1064 on 2012-05-10
> **rulet said:**
> It's not driver related bug. Just turn off apport.
what you mean turn off approt? how can i do it?

---

### Post by rulet on 2012-05-10
See post 18.

---

### Post by erik1001 on 2012-06-08
del

---

### Post by cdoebbler on 2012-07-25
I get these repeated 'internal error' messages and the system appears to crash in so far as it bumps me back out to login (ie it does not restart). Moreover when I click to report the error it does not seem to report it. These 'resets' are occurring roughly 20 times a day.

---

### Post by bcschmerker on 2012-08-16
In my case, as I am configuring a rebuilt eMachines®/Acer® EL1210-09 slimline with Asus® EN210/DI/512MD2(LP) PCI-Express x16 add-on video and Shuttle® PC6300002 PSU for projection-computer duty, I noticed that the "internal error" statements from Apport occur at on or about the same frequency as the cache-retrieval errors when I was fixing X from the Console immediately post-installation (which I anticipated having to do, as installations don't always go smoothly with so oddball a hardware combination as an Advance Micro Devices® Athlon® LE-1620 CPU; nVIDIA® MCP78S chipset with GeForce® 8200 planar and GeForce® 210 add-on GPU's; and Realtek® LAN and audio).

About what percent of these "internal error" scenarios can be chalked up to a Kernel 3.2 oops due to unusual hardware consists?

---

### Post by bcschmerker on 2012-08-30
> **bcschmerker said:**
> In my case, as I am configuring a rebuilt eMachines®/Acer® EL1210-09 slimline with Asus® EN210/DI/512MD2(LP) PCI-Express x16 add-on video and Shuttle® PC6300002 PSU for projection-computer duty, I noticed that the "internal error" statements from Apport occur at on or about the same frequency as the cache-retrieval errors when I was fixing X from the Console immediately post-installation....**Update:**  I found from another Thread that the cache-retrieval-error statements were a side effect of Kernel 3.2 secondary-storage management and not necessarily related to the Internal Error issue.  When the Kernel fails to retrieve cache from an HDD or optical drive, it proceeds as though the device uses a write-through cache.

---

### Post by PikoMedia on 2012-12-16
> **Dennis N said:**
> Just Apport doing its job. It generates crash reports for debugging purposes. 

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

From reading this, and looking at the relevant file, it can be disabled if desired by setting enabled=0 in /etc/default/apport
Thanks DennisN for the tip on disabling Apport. I fully support providing details to the heroic people who fix bugs, but as this message pops up 4 or 5 times or more per session, it simply gets too annoying for me.

---

