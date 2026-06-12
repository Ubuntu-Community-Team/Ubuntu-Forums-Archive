---
title: "No wireless capability after installation"
date: 2010-09-03
forum: General Help
---

### Post by Saultaylor on 2010-09-03
Hi guys,
 
I have just installed 10.04 on my laptop Acer Aspire 5551-A and found that ubuntu is not recognising my network adapter (the wireless light is off). I have had a look around these forums for help but am relatively new to Ubuntu and can't get a handle on how to fix this. Can anyone help me?
 
Thanks!

---

### Post by llamabr on 2010-09-03
You have an adapter?  Or you mean the internal wireless?

If the former, what is the model?

[http://ubuntuforums.org/showthread.php?t=573332&page=2](http://ubuntuforums.org/showthread.php?t=573332&page=2)

---

### Post by blazemore on 2010-09-03
When you say it's not detected, do you mean it says no network devices are present, or that it is detected, but doesn't show any networks?

---

### Post by soresger on 2010-09-03
> **blazemore said:**
> When you say it's not detected, do you mean it says no network devices are present, or that it is detected, but doesn't show any networks?

I have the same problem.

I have a Belkin USB adapter and it is not detected by Ubuntu 10.10.

---

### Post by blazemore on 2010-09-03
> **soresger said:**
> I have the same problem.

I have a Belkin USB adapter and it is not detected by Ubuntu 10.10.

Which of the two issues I described are affecting you.
They are separate problems with separate solutions.

---

### Post by soresger on 2010-09-03
> **blazemore said:**
> Which of the two issues I described are affecting you.
They are separate problems with separate solutions.

>No network devices are present.

---

### Post by JohnElway on 2010-09-03
If your wireless device is not detected, it's usually, but not always, because you don't have the drivers for the device installed. To get them just setup a wired connection between your computer and your wireless router, then go to System>Administration>Hardware Drivers and you should see a driver for your wireless device. Click "Activate", let it download and install the driver, then reboot. If you don't see anything in Hardware Drivers, make sure you have all the latest updates installed on your system and check again.

In rarer cases, Ubuntu won't recognize your ethernet card either, meaning you won't even be able to setup a wired connection (this happened on one of my 3 computers). In this case, you need to download the driver and firmware from another computer and install it on your computer "manually". Although I wouldn't worry about it until you're certain you can't setup a wired connection.

---

### Post by soresger on 2010-09-03
> **JohnElway said:**
> If your wireless device is not detected, it's usually, but not always, because you don't have the drivers for the device installed. To get them just setup a wired connection between your computer and your wireless router, then go to System>Administration>Hardware Drivers and you should see a driver for your wireless device. Click "Activate", let it download and install the driver, then reboot. If you don't see anything in Hardware Drivers, make sure you have all the latest updates installed on your system and check again.

In rarer cases, Ubuntu won't recognize your Ethernet card either, meaning you won't even be able to setup a wired connection (this happened on one of my 3 computers). In this case, you need to download the driver and firmware from another computer and install it on your computer "manually". Although I wouldn't worry about it until you're certain you can't setup a wired connection.

@JohnElway

I can not setup a wired connection because my router is far from my computer and I don't have an Ethernet cable that is long enough to perform plugging it into my computer's Ethernet port and the router's port.

Can you please explain how I can manually download the drivers (I am using Windows XP right now) to my Windows XP so that I can copy it and boot up in Ubuntu and install it there and what are the commands to install the driver I downloaded?

My wireless adapter is a Belkin RTL81915

---

### Post by David Batty on 2010-09-03
I had to install the following to get my Belkin USB working which  [slughappy1]("http://ubuntuforums.org/member.php?u=341209")  had put this info on an earlier post. hope it works for you.

1- You must have the rt2870.inf and the rt2870.sys from the xp x64 driver, which you can get from the Driver CD that came with. Copy the two files to a folder somewhere on your computer.
2- Open a terminal and type....
3- "sudo apt-get update && sudo apt-get install ndisgtk && sudo ndisgtk" but take the quotes out
4- A GUI will pop up. Click on Install New Driver and go to the location of your rt2870.inf and the rt2870.sys and select the .inf file, click install
Reboot and you should be online. You may have to enter your ESSID and password.

---

### Post by JohnElway on 2010-09-03
In a terminal type:

```
lspci
```and post the output here.

EDIT: This is directed at soresger.

---

### Post by soresger on 2010-09-04
Hi @JohnElway.

> soresger@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
soresger@ubuntu:~$ 

When I type lsusb I can see my adapter but it is no use to me.

---

### Post by soresger on 2010-09-04
> **David Batty said:**
> I had to install the following to get my Belkin USB working which  [slughappy1]("http://ubuntuforums.org/member.php?u=341209")  had put this info on an earlier post. hope it works for you.

1- You must have the rt2870.inf and the rt2870.sys from the xp x64 driver, which you can get from the Driver CD that came with. Copy the two files to a folder somewhere on your computer.
2- Open a terminal and type....
3- "sudo apt-get update && sudo apt-get install ndisgtk && sudo ndisgtk" but take the quotes out
4- A GUI will pop up. Click on Install New Driver and go to the location of your rt2870.inf and the rt2870.sys and select the .inf file, click install
Reboot and you should be online. You may have to enter your ESSID and password.

Doesn't seem to work. Attempts to try and connect to the Internet (server) to download certain files. It fails.

---

### Post by soresger on 2010-09-04
Still no hope.

**I am wondering if I should install an earlier version of Ubuntu instead of the beta version. Would you also suggest this?**

Also Internet works in **VirtualBox** (Ubuntu 10.10)

Edit: I am downloading **Ubuntu 10.04.1** desktop now.

Will reply if wireless works in that version of Ubuntu.

---

### Post by blazemore on 2010-09-04
> **soresger said:**
> Doesn't seem to work. Attempts to try and connect to the Internet (server) to download certain files. It fails.

Well obviously, because the wireless isn't working!
Connect with a wire or with another adaptor to install the required packages.

---

### Post by soresger on 2010-09-04
> **blazemore said:**
> Well obviously, because the wireless isn't working!
Connect with a wire or with another adaptor to install the required packages.

I don't think you are reading my posts!

[http://ubuntuforums.org/showpost.php?p=9803337&postcount=8](http://ubuntuforums.org/showpost.php?p=9803337&postcount=8)
> 
I can not setup a wired connection because my router is far from my  computer and I don't have an Ethernet cable that is long enough to  perform plugging it into my computer's Ethernet port and the router's  port.

---

### Post by blazemore on 2010-09-04
Download the following 2 deb packages on Windows:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.56-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.56-2_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56-2_i386.deb)

Then download the Windows XP driver from Belkin's website.
Install those three deb packages on Ubuntu.

Once you've done that, follow the instructions in my post here:
[http://ubuntuforums.org/showthread.php?p=9782853#post9782853](http://ubuntuforums.org/showthread.php?p=9782853#post9782853)

---

### Post by soresger on 2010-09-04
Hello,

I followed your instructions but it has not worked yet again.

---

### Post by OpressedCalamity on 2010-09-04
> **soresger said:**
> I have the same problem.

I have a Belkin USB adapter and it is not detected by Ubuntu 10.10.

Good luck getting any Wireless USB adapter working with Ubuntu.
If windows vista can do it, why can't Ubuntu? lol.
the so called easy to use operating system.

---

### Post by soresger on 2010-09-04
> **OpressedCalamity said:**
> Good luck getting any Wireless USB adapter working with Ubuntu.
If windows vista can do it, why can't Ubuntu? lol.
the so called easy to use operating system.

Most drivers are created for Windows OS. That is the reason. Also there is more support for Windows than Ubuntu.

---

### Post by nagaprathyush on 2010-09-04
I used to think that ubuntu doesnt support my lenovo laptop's wireless adapter as well :D, when I installed it a month or so back..... until recently a few days back, I found out that there is a keyboard shortcut for my laptop "Fn+F4" to enable wifi and "Fn+F5" for bluetooth, I had to enable them by pressing these keyboard keys after turning my wifi on. I did'nt know if it was always ON my windows ...lol

If at all the adapter is recognized(irrespective of on or off state of adapter), the command 
***ifconfig -a***
should show you all the available interfaces..... eth0 or wlan0 or whatever it is for you.....
Hope that helps....

---

### Post by soresger on 2010-09-04
> **nagaprathyush said:**
> I used to think that ubuntu doesnt support my lenovo laptop's wireless adapter as well :D, when I installed it a month or so back..... until recently a few days back, I found out that there is a keyboard shortcut for my laptop "Fn+F4" to enable wifi and "Fn+F5" for bluetooth, I had to enable them by pressing these keyboard keys after turning my wifi on. I did'nt know if it was always ON my windows ...lol

If at all the adapter is recognized(irrespective of on or off state of adapter), the command 
***ifconfig -a***
should show you all the available interfaces..... eth0 or wlan0 or whatever it is for you.....
Hope that helps....

I get a message saying that there is no such interface or no such device.

I think I will just regretfully uninstall Ubuntu and keep Windows as I have no other choice ;(

---

### Post by JedMeister on 2010-09-04
> **soresger said:**
> I can not setup a wired connection because my router is far from my computer and I don't have an Ethernet cable that is long enough to perform plugging it into my computer's Ethernet port and the router's port.Why not just move your computer closer then? I know its a bit of a pain but surely not that big a deal? IMO that is your best plan as a first step. On the 4 or 5 systems I've installed 10.04 on, plugging it in has got wifi working in moments.
> **soresger said:**
> **I am wondering if I should install an earlier version of Ubuntu instead of the beta version. Would you also suggest this?**Yes! You may well still encounter the same issue but unless you use a released version then you'll never know and it may just be a beta bug. Thing is though you will still have this same issue because AFAIK Ubuntu does not come with wifi drivers, you need to plug your cable in first run and download them!
> **soresger said:**
> Also Internet works in **VirtualBox** (Ubuntu 10.10)No great surprise there as VBox uses a Virtual Interface (not the real hardware one) so as far as its concerned its plugged in with a wire!
> **soresger said:**
> Hello,
I followed your instructions but it has not worked yet again.You didn't give any details of what went wrong? Did you follow all the steps as laid out? Which steps didn't work? What problems/errors/etc did you encounter?
> **soresger said:**
> I think I will just regretfully uninstall Ubuntu and keep Windows as I have no other choice ;(Sometimes it comes to that, but I would encourage you to either move your PC so you can plug it in, or try to troubleshoot why blazemore's instructions aren't working - because they should!

---

### Post by soresger on 2010-09-04
@Jedmeister,
 
Can you suggest another linux distribution that has wireless drivers already set, such as FreeBSD or an alternative?

---

### Post by JedMeister on 2010-09-05
> **soresger said:**
> @Jedmeister,
 
Can you suggest another linux distribution that has wireless drivers already set, such as FreeBSD or an alternative?I can not speak from experience but I would imagine that distros designed to run as a LiveCD (ie not installed to HDD) would have a better chance of included drivers (although I'm guessing really). 2 that spring to mind are PuppyLinux and Knoppix. Puppy I've used before but not a lot and don't recall whether I had any joy with auto wifi drivers. Its only a small download so possibly not a lot of drivers? Its aimed at low spec machines so does not have all the bells and whistles. Knoppix I've never used but does come as a DVD apparently (which suggests it may have lots of drivers?)

A quick google suggests that PCLinuxOS has pretty good auto driver support. I used it a while ago and its quite a nice distro although I found the rolling release frustrating (new stable versions are never released, everything is constantly updated). Considering how unstable it could potentially be it was a lot better than I expected but I still found strange things happened unexpectedly and random glitches occurred (then often disappeared again). That's not to say Ubuntu is perfect but I find it more stable and predictable (and when odd things happen they are often easier to track down). I have also read that Linux Mint (based on Ubuntu) has better wifi support than Ubuntu itself (but I can't vouch for that). OpenSUSE may be another that has a DVD that includes wifi drivers but I am unsure and I have never used it (mostly out of protest re the MS-Novell deal). BackTrack may be another option (liveCD distro) but as it is specifically security/hacking focused I'm not sure how useful it'd be as a desktop system.

Bottom line is that most Linux OSs assume you will be able to access the internet via cable to download your wifi drivers. I still don't understand why you don't move your PC to plug it in to your router. I bet you'd have this problem fixed 10 times over in the time its taken you post on here and all the other stuff you've probably tried. 

Also it doesn't seem like you put a lot of effort into trying blazemore's steps to use ndiswrapper, I'm sure we could get that to work with a little troubleshooting you just need to give some details of the problems you're having.

IMO unless you want to waste days downloading distros and burning them to CD/DVD, installing and possibly encountering the same (or similar) problems, either try the 2 suggestions I mention (move PC or retry blazemore's steps). Or give up on Linux and return to Windows.

---

### Post by soresger on 2010-09-05
> **blazemore said:**
> Well obviously, because the wireless isn't working!
Connect with a wire or with another adaptor to install the required packages.

Can you tell me the best compatible N or N+ adapter so I can buy one from ebay etc?

---

### Post by soresger on 2010-09-05
> **blazemore said:**
> Download the following 2 deb packages on Windows:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.56-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.56-2_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56-2_i386.deb)

Then download the Windows XP driver from Belkin's website.
Install those three deb packages on Ubuntu.

Once you've done that, follow the instructions in my post here:
[http://ubuntuforums.org/showthread.php?p=9782853#post9782853](http://ubuntuforums.org/showthread.php?p=9782853#post9782853)

You have given the links for 3 packages. I thought there was only 2? This is confusing as it is..

---

### Post by JedMeister on 2010-09-06
> **soresger said:**
> Can you tell me the best compatible N or N+ adapter so I can buy one from ebay etc?TBH I have no idea, perhaps create a thread asking others. Or maybe its easier to go the other way, find a couple that are going for a fair price, find out what chipset they use and research whether Linux/Ubuntu support them ok. Or if you are looking for a distro that will include the drivers then I suggest you find out what drivers are included in which distro, which chipsets they support and then which products have those chipsets. I haven't got a link handy but I've come across a few places where there are lists of hardware with good Linux support.> **soresger said:**
> You have given the links for 3 packages. I thought there was only 2? This is confusing as it is..I suspect that was a typo. Try downloading all 3, then install them in Ubuntu (double click should do the trick). I'm not sure but I think the order blazemore set them out is the order they will need to be installed. If there are any problems, _**do not give up**_! Just copy and paste the exact error message into a text document (somewhere where Windows can access it, ie not in your Ubuntu directory) and post it here.

PS to make life easier for yourself, it may be useful to save all the relevant webpages so you can view them in Ubuntu (rather than having to go back and forth from Win to Ubuntu to read up the next bit). Good luck.

---

### Post by soresger on 2010-09-10
Thank you all guys for helping me out. I bought a long Ethernet cable and I am going to see if making this direct connection through Ethernet is going to solve the problem.

You have all been very patient when answering my beginner questions and have indeed helped me out very much.

---

### Post by JedMeister on 2010-09-11
> **soresger said:**
> Thank you all guys for helping me out. I bought a long Ethernet cable and I am going to see if making this direct connection through Ethernet is going to solve the problem.No worries! I really hope it does! I suspect it will - and hey otherwise you'll have a nice long LAN cable to connect with anyway :)

> **soresger said:**
> You have all been very patient when answering my beginner questions and have indeed helped me out very much.That's what the forums are here for! 

Just keep in mind that the first thing you want to try is System>>Administration>>Hardware Drivers. If that doesn't find anything (hopefully it will and it will all work lovely and automatically), don't despair. If you still have no wifi, go to Synaptic Package Manager (again in System>>Administration) and install "ndiswrapper" (use the search box to find it). Also download your wifi's Windows XP drivers from the manufacturer's website. Then follow the instructions in [blazemore's link]("http://ubuntuforums.org/showthread.php?p=9782853#post9782853") (you don't have to download the 3 files he mentioned earlier - Synaptic should have done that for you).

Any dramas, let us know here.

---

### Post by soresger on 2010-09-16
Hi JedMeister and all.

I removed Ubuntu 10.4 from my hard disk and I downloaded and installed the latest Ubuntu 10.10 Maverick Meerkat inside Windows, so now I can dual boot :KS!

I connected the Ethernet cable and voilia it worked like a charm! I am now using Ubuntu 10.10 whith which I connected to the internet to write on this forum. Firefox is working better in Ubuntu than it works in the Windows environment and it is much much faster with almost no bugs/crashes at all. Edit: and now I installed Chromium web browser which is even better. Totally recommendable browser for Ubuntu linux!

Thank you so much. I should of listened to your instructions in the very first place hehe :D

I recommend everybody else to do the same if they are unsuccessful installing their drivers for the usb network adapters. It certainly is a 100% working method :) It worked for me, there is no reason why it shouldn't work for you!

---

### Post by soresger on 2010-09-16
Should I install any codecs or other packages? Which packages are useful to install?

---

### Post by JedMeister on 2010-09-16
Glad its all working sweet for you!
> **soresger said:**
> Should I install any codecs or other packages? Which packages are useful to install?That's entirely up to you and whether you want to watch DVDs on your Ubuntu PC and/or listen to MP3s and/or etc, etc. Personally I do! I usually install them using the Medibuntu repo. Have a look [here]("https://help.ubuntu.com/community/Medibuntu"), should head you in the right direction!

---

### Post by soresger on 2010-09-16
Thank you for the advice :) I hope other beginners are also reading this thread and are getting an idea to resolve the problems they are experiencing that are similar to mine.

---

