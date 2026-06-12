---
title: "System freezes (apparently) at random"
date: 2011-03-08
forum: General Help
---

### Post by Pronker on 2011-03-08
Hi guys, I just recently made a clean ubuntu install with wubi (inside windows) but I've had several incidents where the entire system froze (i.e. unable to move curser and system non-responsive to _any_ keyboard input) - I had to hold off button to turn pc off. 

This has happened right since the beginning - I have only installed dropbox and skype from outside (and later adobe reader).

I have a hunch: Right from the beginning I've been logging on to the University of Melbourne's wireless network. This is a WPA2 network with PEAP login and moreover it requires using a password protected proxy server (i.e. you can always access sites *.unimelb.edu.au but to access external you need to set up the proxy and when you go online it will ask for your password). 
Hence, I use gnome-network-preferences to set the proxy system-wide. Today I had three crashes in a row but then I switched the proxy back on and the crashes stopped. 

Does anyone have any ideas as to what could be ******* up?

Other relevant info:
PC: Sony Vaio C-series (VPCY11S1E)
Have used VPNC as well as email (which had to fetch 2000+ emails from hotmail - took a long time but it hasn't been going all the time)
The windows install holding ubuntu (@ wubi) is Windows 7 64-bit
Ubuntu is standard 32-bit.

---

### Post by TimmyK. on 2011-03-08
I had a computer running Win XP which crashed constantly every time you used it, so I know how frustrating it is.

If this is a software problem, I wouldn't know what to do besides reinstall the OS. 

If this is a hardware problem, there can be one of several things you can do. Take the heat sink off of your CPU and see if there is any liquid heat paste still in there. If it is all dried up, you need to get some more. If the fan is busted, then you need to replace it. 

Or, in a worst-case scenario, you may have a heat sink that does not completely cover the CPU. I have a computer like this that had a square CPU and a round heat sink, and it ran so slowly and constantly crashed. The usual CPU temperature reading was around 97 C. If this is the case, you need a new heat sink.

---

### Post by Pronker on 2011-03-08
@TimmyK
Thanks man, but it's a laptop and I kind of suck at fisting around in it so I don't think it's an option for my (unless all else fails) :S

I've now had a crash even though the proxy was set up the same way as previously so I'm ruling that one out. 
My main suspect is now the "NetworkManager" that comes with ubuntu... I'm going to try reverting to using e.g. dhclient instead... just gotta figure out how to set it up to connect to the network and I'm good. I'll post what happens.

EDIT: Trying out this guide... fingers crossed! [http://www.codealias.info/technotes/wireless_security_wpa/wap2_with_eap-peap_using_wpa_supplicant_and_client_ssl_certificates_linux_setup#comment__417a43b2c013565c40d52b2111730346](http://www.codealias.info/technotes/wireless_security_wpa/wap2_with_eap-peap_using_wpa_supplicant_and_client_ssl_certificates_linux_setup#comment__417a43b2c013565c40d52b2111730346)

---

### Post by Pronker on 2011-03-10
This apparently solved the problem! If anyone competent in the noble art of submitting bugs is reading this, please let the guys writing the network manager applet know that there is a _serious_ stability issue... 
I think the problem is that with this UniWireless thing the computer keeps logging on and off the wireless network. With Windows it's (obviously) even worse -- it keeps asking people to re-enter their password and after some apparently random number of times it accepts it and allows them access to the network. Then it will all of a sudden log off the network again later. 

Anyways, using the good ole command line is apparently (as usual) the most stable way to go.
Hope this helps anyone else having the same kind of trouble out there!

(by the way, the network is a WPA2 (enterprise) PEAP using MSCHAPV2 authentication. Furthermore, a proxy server which requires authentication as well is employed on campus (I access this using the ubuntu system-wide proxy settings which also allows specifying a username and password))

---

### Post by Pronker on 2011-03-16
Nope, still having trouble:(

I am now almost positive that the problem is related to my wireless driver -- after having worked for 5 hours with no problems, I moved from one area to another on campus and my pc crashed (I carried it while it was turned on)... it must've lost connection or something.

Any ideas would really be appreciated, I don't want to go back to windows! And it's not a hardware problem because I have no such issues in windows. 
It might also be that I've installed linux inside windows (using wubi) and that the NTFS drivers are causing trouble.

Are there any log files that might be relevant? What should I look for??

---

### Post by Pronker on 2011-03-17
Anyone?

I'm now positive that the problem is related to the wireless driver. I turned it on at campus, tried to connect to the net and after attempting for ~1min, it froze. Afterwards, I just worked on it while offline for 2½ hours with no interruptions where I didn't touch the wireless... 

Also, no flashing capslock or numlock key, so it isn't a kernel panick!

I've tried following this: [http://ubuntuforums.org/showthread.php?t=1203004](http://ubuntuforums.org/showthread.php?t=1203004)
and install linux-backports-modules-wireless-maverick. Will report back what happens...

---

### Post by Pronker on 2011-03-18
WUHUU!!! I'm back in business!!! (hopefully;)

After struggling and crying like a little bitch, I found out what was wrong (at least no crashes the past 20mins :P lol

The native Atheros driver is horribly bugged:( I recommend anyone experincing the same problem to follow the same steps and take care not to **** up your ubuntu install too much on the way! (remember to figure out how to undo whatever you do -- I still haven't got a network manager anymore;)

Fetch the correct Atheros driver from atheros.cz, mine was for the Atheros AR9285. You should fetch the *.inf file but you might have to get a big *.zip folder, unzip it to get the netathw.inf file.
apt-get install ndisgtk.
alt+F2 gksu ndisgtk.
Install the inf module. 
Restart and pray to God.

Mine didn't work right away, in that case refer to the brilliant comprehensive ndiswrapper troubleshooting guide ([http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)). I first tried the XP 9.* version which failed miserably (I ran "dmesg | grep -e ndis -e wlan" and found the words "unknown symbol"). The XP 7.* version worked perfectly...

Good luck! And guys, it's worth the fight to be back with ubuntu -- she can be a hag but you know she's good! *smack*

---

### Post by adamf4i on 2011-03-18
I recently installed ubuntu and mine seems to lock up/ freeze to where you have to hard boot it . Im not familar with linux OS at all just trying to use it all the time now over windows . Any suggestions for why it is freezing? and what i can do?

---

### Post by Pronker on 2011-03-18
What kind of computer are you using? It'll probably take you a few hours to solve the problem, but believe me; it's worth the wait!

next time it happens, check whether your capslock and numlock keys are flashing. If so, you're looking at a kernel panick and you have to figure our which module is causing you trouble. If it isn't, it sounds like it's the same problem I had. Check out what card type you have (Applications -> Accessories -> Terminal, and hit lshw -C Network and look for the wireless one). If it's called Atheros AR9285 then you're in the same boat as me. Just follow the steps mentioned above (although, make sure you have access to some internet by some other means cause it'll be gone while you're fiddling around under the hood!)

---

### Post by adamf4i on 2011-03-18
Its a desktop custom build 

It doesnt have wireless so its directly connected and its working . Just will freeze up.

---

### Post by Pronker on 2011-03-18
goddamn... linux, thou art a heartless beatch! 

I just had another system freeze -- ubuntu had been running for 5 hours straight with no problems and lots of internet access. I shut it down, reboot it later and after being up for some 1-2mins it freezes again... still no flashing capslock, so not a kernel-panick-ish thing. It appears it wasn't the wireless driver after all! But it's related to being on the wireless net somehow, I'm absolutely sure of it! It froze just 30sec after I got connected to the wifi at my house. 

I'm writing from my windoze install now... it hurts, but ubuntu, you may not be the right one for me after all! Unless someone can come with some help soon!

---

### Post by Pronker on 2011-03-19
*sobs*

---

### Post by Pronker on 2011-03-24
Oh, by the way, I'm running a 32-bit install on a 64-bit machine, could that give any problems? I've installed the 32-bit inside a 64-bit windows using wubi...

---

### Post by Pronker on 2011-06-03
(in the event that someone else is following this and having the same problems)

I read about a guy having similar problems (although his freezes happened _at_ boot, i.e. he didn't even get to the login screen): [http://ubuntuforums.org/showthread.php?p=10896223#post10896223](http://ubuntuforums.org/showthread.php?p=10896223#post10896223) 

I'll try ubuntu 11.04 instead and see if it works.

---

### Post by techunit on 2011-06-03
Hi are you trying to install with the same Ubuntu CD every time? You may have burned it incorrectly and are consequentially missing packages that are nessissary for stability. I saw your post on your blog and am here to investigate. I doubt very much it has anything to do with the wireless.

---

### Post by Pronker on 2011-06-04
Hi thanks for the reply! I've installed using Wubi (i.e. inside my windowspartition). It is possible that something hasn't been downloaded properly -- I don't know if there's some way of verifying the installation? Anyway, if it is indeed a faulty installation do you think it would help to do a dist-upgrade? And in that case how? Back in the days of Edgy Eft I had trouble with dist-upgrade as it didn't properly upgrade anything but if I use the gui (synaptic, I guess?) maybe things run more smoothly these days? That is, assuming it will run for long enough without freezing to allow me to do the upgrade. 
Because faulty installation sounds to me like much more plausible explanation than what I've been able to come up with. Plus I experienced a crash at one point where wiereless wasn't even on.

Anyway, thanks for your help! This helpfulness is what I love about linux and what I hate about windows!

---

### Post by Pronker on 2011-09-23
I'm back again. Finally had the time to try to reinstall linux. I rolled out a fresh instllation of linux mint 11 and at the first boot the system froze in the same way described above. The only thing out of the ordinary that I noticed was that wifi didn't work out of the box this time -- when I clicked the newtork manager applet it said "wifi disabled by hardware switch" (which it definitely wasn't!) and I couldn't fix it so I plugged in the ethernet cable. 

The system freeze occured right after the ethernet cable accidentally "slipped" out (it's loose)... I don't know if that means anything, it could just be a coincidence.
The system had been up and running for about 10 mins, although I didn't touch it the first 7 mins or so (so it just locked the screen and I unlocked it again).

The installation was on a 14gb primary partition (ext4), 100mb swap and a 94gb logical partition (ext4, for the /home).

---

### Post by Pronker on 2011-09-23
I stumbled over a guy having a similar problem who "solved" it by adding the option "noapic" to the boot command in grub. I tried it and no crash the past 2 hours+. I'll report back later... fingers crossed!

---

### Post by Pronker on 2011-09-24
No solution apparently. I'm giving up om linux on this laptop permanently after just experiencing another system crash. I booted my system (having verified that the noapic option was on in grub) and after booting I started the wifi (which didn't work with the network manager applet so I did it using iwconfig wlan0 essid mywifi key mypass). Then I started chrome, played around with google's doodle for a short while and then the system froze again (still no flashing numlock etc. -- just a completely nonresponsive system freeze). 

Also, I noticed during almost all previous freezes that some files which I had _definitely_ changed prior to the freeze were at their original state after a forced restart (pressed and held the power button) consistent with the swap space having not unloaded (or whatever it does) before the freeze.

I've encountered several other people with similar problems on VAIO laptops so I'm expecting it to be a bug related to some hardware driver specific to VAIO (once again, my VAIO is a VPCY11S1E).

---

### Post by Stauricus on 2011-09-25
well, i have the same issue on my Lenovo... but in my case, it does not have anything to do the wireless turned on or off. just the ethernet cable. 
someone said that its a bug fixed in recent a kernel, but i don't know if it's true. why don't you try to run Oneiric Ocelot beta 2 from live CD?

by now i'm stuck in windows #-o, and waiting the next Ubuntu stable release.

---

### Post by Pronker on 2011-09-26
> **Stauricus said:**
> 
by now i'm stuck in windows #-o, and waiting the next Ubuntu stable release.

Definitely not a nice situation to be in! Sounds interesting with the kernel trouble... maybe I should try running without wifi and see if I still get the freeze. What wifi card do you have? Mine is an Atheros.

---

### Post by Pronker on 2011-09-26
Hmm, it might actually be this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762496?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762496?comments=all)

Although I don't know how to test it. Is there a way to download a pre-compiled kernel with the updated wifi drivers in without having to specify in detail all sorts of drivers for chipsets I have no clue about?

---

### Post by Stauricus on 2011-09-30
sorry the delay to reply. mine is Atheros too.

about the Kernel i really don't know. i'm a newbie to Ubuntu/Linux. but i'm also looking forward to the answer.

---

### Post by Pronker on 2011-10-05
Progress since last time! I upgraded the kernel and the laptop ran for 6 straight hours with no crash. Then again 3 hours no crash. Then 10mins and a crash and 2mins and a crash the next day :( No crashes since then though. 

I ran uname -a to get my system version right (was something like 2.6.38-8-generic x86_64). Then I installed the new kernel using apt-get install linux-image-2.6.38-11-generic.

According to the launchpad bug report mentioned above the driver should've been fixed from version 2.6.38-9 and forward.

I'm presently trying to think of a way of testing whether it indeed is the wifi causing trouble (the standard ath9k driver is being used by default). As mentioned earlier in this post, I tried using ndiswrapper and the windoze driver and got a crash and immediately discarded the wifi as the source of the problem and gave up... but now I'm no longer sure if the ath9k driver could still have been loaded or been spooking in the background?

---

### Post by Stauricus on 2011-10-21
well, unfortunately i still have this problem with 11.10.
if i have windows 7 (and the atheros drivers) on my HD, it will run Ubuntu Live CD with no crashes! without Windows 7, it crashes.
does it loads the drives BEFORE start the OS?? that's odd. :confused:

any progress, Pronker?


EDIT: ok, now you can forget what i said. it freezes with or without Windows no the HD.

---

### Post by Pronker on 2011-10-21
> **Stauricus said:**
> well, unfortunately i still have this problem with 11.10.
if i have windows 7 (and the atheros drivers) on my HD, it will run Ubuntu Live CD with no crashes! without Windows 7, it crashes.
does it loads the drives BEFORE start the OS?? that's odd. :confused:

any progress, Pronker?


EDIT: ok, now you can forget what i said. it freezes with or without Windows no the HD.

Nah I ended up giving up. Installed ubuntu mint on another laptop and it ran with no problems whatsoever. Uograding the kernel should have helped according to the launchpad bug I mentioned but no help. I am however almost 100% certain that the problem has to do with the faulty atheros driver. If you want to test this, one thing that might show it is if you type in terminal: sudo rmmod ath9k_common ath9k ath ath_wireless (type lsmod | grep ath and basically rmmod everything... Note that the sequence you rmmod is important!). Then leave it running. My guess is that then it wont die.

One other option is to build your own kernel (google vanilla kernel) and make sure that no atheros driver is built in. Then install ndiswrapper and install the windows atheros driver in that one.

But really, the kernel developers ought to get their fingers out (with all due respect to those awesome guys)...

---

### Post by Stauricus on 2011-10-25
well, so there's a place where we can report this to the kernel development team? so we can notify them about it and maybe help to fix it?
i actually don't know, as i'm new to Ubuntu (and Linux). too bad i'm having these issues...

---

### Post by Hylas de Niall on 2011-10-26
Second freeze on my Aspire desktop in just over a week(OO, Gnome shell, no wi-fi).
Not frequent enough yet to worry, but it's awkward having to cold-boot when that happens.

---

### Post by Pronker on 2011-10-27
@Stauricus: I'm pretty sure there is a place to do it, I just feel like you have to be a pro to know how to do it. Also, I uninstalled linux from that laptop because the problems were too severe and too frequent:S so I wouldn't be able to provide debugging info if they started requesting it. Sorry to hear you get such a rough start:( But hang in there, it's well worth it when it works! 

@Hylas de Niall: Odd, try updating your kernel (as I described above) and see if that works. Also, do you have an atheros card? ("lspci  | grep ath" or "lsmod | grep ath")

---

### Post by Pronker on 2011-10-27
If your problem is wifi related, maybe try something like these solutions: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034)
[https://bugs.launchpad.net/linux/+bug/426130](https://bugs.launchpad.net/linux/+bug/426130)

---

### Post by mbn18 on 2011-10-31
After I upgrade my Ubuntu from 11.04 to 11.10 I had the following issue.
[LIST]
[*]My upgrade Ubuntu 11.10 kept freezing randomly.
[*]Had long delays while booting.
[*]Shutdown kept freezing from time to time
[/LIST]

I have no idea why. I explored the forum and net with no luck and the syslog was not useful in discovering the cause. My hardware is quite decent. Intel 930 I7 and gigabyte MB + 8GB RAM.

I did solved the problem by installing the server kernel
```
sudo apt-get install linux-image-3.0.0-12-server linux-headers-3.0.0-12-server
```

Now its the second day without any freeze. The boot still has long delays, though I can live with it.

Hopes it helps :D

---

### Post by Pronker on 2011-11-01
> **mbn18 said:**
> 
[LIST]
[*]My upgrade Ubuntu 11.10 kept freezing randomly.
[*]Had long delays while booting.
[*]Shutdown kept freezing from time to time
[/LIST]
Hopes it helps :D

Happy to hear that you're runing without problems now! Hope it keeps working for you! What wireless card do you have? (just for comparison). Brilliant idea with the server kernel -- I didn't think of that!

I had a quite fast boot though...

---

### Post by mbn18 on 2011-11-01
> **Pronker said:**
> Happy to hear that you're runing without problems now! Hope it keeps working for you! What wireless card do you have? (just for comparison). Brilliant idea with the server kernel -- I didn't think of that!

I had a quite fast boot though...

Yep it keep working :) no crashes.

Here are my net devices:
```

$ lspci |grep -i net
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:04.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI

```

---

### Post by dh003i on 2011-12-07
I have a similar problem with random clustered freezes for a second or two (although the system recovers). Perhaps I should also install the server kernel? Except for the GPU, these are all server-grade components:

Motherboard: Supermicro H8DG6-F
CPUs: 2 x AMD Opteron 6128
RAM: each CPU socket has 4 x 8 GB RAM sticks. RAM is KVR1333D3LD4R9S/8GEC 8GB 1333MHz DDR3 ECC Reg CL9 DIMM Low Voltage Server Memory
GPU: Sapphire Radeon FLEX HD6950 2G DDR5 PCIE (ATI Radeon HD6950)


> **mbn18 said:**
> After I upgrade my Ubuntu from 11.04 to 11.10 I had the following issue.
[LIST]
[*]My upgrade Ubuntu 11.10 kept freezing randomly.
[*]Had long delays while booting.
[*]Shutdown kept freezing from time to time
[/LIST]

I have no idea why. I explored the forum and net with no luck and the syslog was not useful in discovering the cause. My hardware is quite decent. Intel 930 I7 and gigabyte MB + 8GB RAM.

I did solved the problem by installing the server kernel
```
sudo apt-get install linux-image-3.0.0-12-server linux-headers-3.0.0-12-server
```

Now its the second day without any freeze. The boot still has long delays, though I can live with it.

Hopes it helps :D

---

### Post by mbn18 on 2011-12-08
> **dh003i said:**
> I have a similar problem with random clustered freezes for a second or two (although the system recovers). Perhaps I should also install the server kernel? Except for the GPU, these are all server-grade components:


Few days after the computer crashed again and again. I had enough so I just installed Fedora F16.
Pity, I like the Debian feel of Ubuntu and the huge availability of apps. But then again Linux suppose to be stable and the last month reminded me the days of win95.

---

### Post by lz1dsb on 2012-01-28
Did you guys try this out:
when there's a hang press Ctrl+Alt+F1 this will get you into a console session. Than login. To get back into the desktop session Ctrl+F7. This is how I got myself out of freeze situations several times...

---

### Post by Pronker on 2012-01-30
Hey lz1dsb, thanks for the idea but I already tried that and it didn't work... there's also the option of pressing ctrl+alt+backspace in some situations like that which will restart X.

---

### Post by markymark64 on 2012-02-08
Folks, this sounds like the same problem I have and I believe the culprit is...drumroll please... flash! Yup, adobe flash. It happened a few times before and it's very random. This usually happens when adobe runs an incompatible, or corrupted update to their flash app. I know it's flash because I diagnosed the problem about six months back when it first happened. Unfortunately, I don't know how to fix it. Adobe has to fix it and they're usually aware long before us of their faux pas. Let me know if anyone else came this same conclusion? Oh and clearing the flash cache and/or deleting the macromedia folder in the home directory doesn't provide a permanent fix. The fix lasts about five minutes. Oh, and yes, the problem is random. Everything works fine for hours but suddenly you launch an application that interacts with flash and your system starts locking up. See. So it's not your wireless card, or a hardware problem, which is why you won't find any errors. It's flash.

---

### Post by Stauricus on 2012-03-06
> **markymark64 said:**
> Folks, this sounds like the same problem I have and I believe the culprit is...drumroll please... flash! Yup, adobe flash. It happened a few times before and it's very random. This usually happens when adobe runs an incompatible, or corrupted update to their flash app. I know it's flash because I diagnosed the problem about six months back when it first happened. Unfortunately, I don't know how to fix it. Adobe has to fix it and they're usually aware long before us of their faux pas. Let me know if anyone else came this same conclusion? Oh and clearing the flash cache and/or deleting the macromedia folder in the home directory doesn't provide a permanent fix. The fix lasts about five minutes. Oh, and yes, the problem is random. Everything works fine for hours but suddenly you launch an application that interacts with flash and your system starts locking up. See. So it's not your wireless card, or a hardware problem, which is why you won't find any errors. It's flash.

no, in this case it's really the driver. my pc does not work fine for hours, it always freezes on startup, IF no ethernet cable is connected. i don't even have enough time to launch any application...
still looking for an answer...

---

### Post by davidvandoren on 2012-03-06
I have the same problem with crashing applications and locking out, freezes etc.
It starts mostly after some time.
My system is 
MSI H55M-E33 motherboard 
4 gigabytes of ram
I3 intel CPU with four threads.

I tried to fix the prolem for over a year now and think that I found the problem.

I have changed my video card several times from Nvidia 220 o the onboard graphics and to an new NVIDA card 430 GT.

I installed on a sata drive  then on an IDE drive, changed the settings for the sata from IDE AHCI.

I tried to disable th on board sound card, Ethernet etc. No use.


Now I watched the memory more closely and noticed that the crashing starts when the memory cache builds up. 

So I executed this ```
sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
```

It seemed to help but one time the whole system froze while doing this. 

Last I changed the CPU I3 Intel in the bios from multi to just one thread per core. 

I haven't had any crashes since then. However, I still watch my memory and
Execute this ```
sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
```

when it gets too much. 

But my xserver log is full of messages now.

---

### Post by davidvandoren on 2012-03-06
I have the same problem with crashing applications and locking out, freezes etc.
It starts mostly after some time.
My system is 
MSI H55M-E33 motherboard 
4 gigabytes of ram
I3 intel CPU with four threads.

I tried to fix the prolem for over a year now and think that I found the problem.

I have changed my video card several times from Nvidia 220 o the onboard graphics and to an new NVIDA card 430 GT.

I installed on a sata drive  then on an IDE drive, changed the settings for the sata from IDE AHCI.

I tried to disable th on board sound card, Ethernet etc. No use.


Now I watched the memory more closely and noticed that the crashing starts when the memory cache builds up. 

So I executed this ```
sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
```

It seemed to help but one time the whole system froze while doing this. 

Last I changed the CPU I3 Intel in the bios from multi to just one thread per core. 

I haven't had any crashes since then. However, I still watch my memory and
Execute this ```
sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
```

when it gets too much. 

But my xserver log is full of messages now.

```
(nautilus:1668): Gdk-CRITICAL **: IA__gdk_window_get_screen: assertion `GDK_IS_WINDOW (window)' failed

(nautilus:1668): Gtk-CRITICAL **: IA__gtk_drag_set_icon_pixmap: assertion `!mask || gdk_window_get_screen (mask) == screen' failed

(nautilus:1668): Gdk-CRITICAL **: IA__gdk_window_get_screen: assertion `GDK_IS_WINDOW (window)' failed

(nautilus:1668): Gtk-CRITICAL **: IA__gtk_drag_set_icon_pixmap: assertion `!mask || gdk_window_get_screen (mask) == screen' failed
```

---

### Post by Pronker on 2012-03-07
Out of curiosity, there is no wireless card installed, right? Also, you don't have flashing caps lock, num lock etc on the keyboard?

---

### Post by davidvandoren on 2012-03-07
> **Pronker said:**
> Out of curiosity, there is no wireless card installed, right? Also, you don't have flashing caps lock, num lock etc on the keyboard?

No, I don't have a wireless card.

Usually the ctrl alt prtsc and typing **r-e-i-s-u-b** still works and restart the system.

I had the flashing caps lock and number lock only twice. 

Did you tryout disabling the multi threading in the bios. 
You can reverse this any time you like.

---

### Post by Stauricus on 2012-03-08
today i tried Ubuntu 12.04 Beta1 on LiveCD, and it worked fine. no crashes, with wireless enabled and disabled.
later i'll try it again. maybe the driver has been fixed. maybe it was just luck.

---

### Post by Stauricus on 2012-03-09
well, it does work only if I start windows, then restart the pc, and start the LiveCD ](*,)

---

### Post by Pronker on 2012-03-10
Hmm that sounds weird.. So does that mean that it has frozen in Linux even in the new version but not of you have booted to windows first?

---

### Post by Pronker on 2012-03-10
> **davidvandoren said:**
> No, I don't have a wireless card.

Usually the ctrl alt prtsc and typing **r-e-i-s-u-b** still works and restart the system.

I had the flashing caps lock and number lock only twice. 

Did you tryout disabling the multi threading in the bios. 
You can reverse this any time you like.

Hmm the flashing caps lock usually indicates a kernel panic.. Maybe the solution for you would be to try a different kernel then? Or to build your own kernel with debug mode enabled to see what goes wrong... Have you looked in the syslog right after crashes? (/var/log/syslog)

---

### Post by Stauricus on 2012-03-10
> **Pronker said:**
> Hmm that sounds weird.. So does that mean that it has frozen in Linux even in the new version but not of you have booted to windows first?

exactly.

news: just tried Fedora 16 with XFCE, and it worked fine. I have booted directly to it, no windows this time.
but again, it may have been just luck. i'll try it later once more.

---

### Post by Stauricus on 2012-03-11
sry fo the double post.

well, it really works with Fedora 16. no freezes.
i'll download Arch Linux and OpenSuSE later.

EDIT: openSUSE does not work either. just for a few minutes.
and i haven't downloaded Arch Linux, as it does not have a LiveCD.

---

### Post by davidvandoren on 2012-04-15
At least for my system I found the culprit.

After my last post on March 6th, I had crashes and reinstalled the system Ubuntu 10.04 with my on-board Audio  Realtek ALC889 disabled in the BIOS. 
I disabled multi thread for my cpu I3 also but I don't think it has anything to do with it. 

I noticed that Alsa Mixer is not installed and when I tried to install it it did not start. 

I am using a 16bit  usb creative sound-blaster  that I bought years ago.


So far, for over a month now, not a single logout, snapping or crashing of applications or any other problem.
The system is running rock solid now. 

But I still would like to figure out, how to get the Realtek ALC889 audio to work without crashing the system. 

Here is a crash I had with Ubuntu and Linux Mint
[IMG]http://ubuntuforums.org/picture.php?albumid=2475&pictureid=8389[/IMG]

Any Ideas? Maybe Alsa or hardware?

---

### Post by Pronker on 2012-08-21
I have now worked in Mint for about a year. I've had similar crashes to what I've reported here but they _NEVER_ occured when the laptop was in a docking station. 

Similar to my previous setup I had no Swap. I now have an installation where I've made a 2gb swap space and it appears that I'm rid of the horrible crashes. Try this if you're having similar issues.

---

