---
title: "Ubuntu 9 &amp; 10?"
date: 2010-09-15
forum: General Help
---

### Post by Quarkrad on 2010-09-15
I have a dual boot 10.04 and winxp system - can I install Ubuntu 9.10 as well?  I have lived with Ubuntu since ver 8 and all has been fine - specially my usb wifi stick.  However, since installing 10.04 I keep getting random disconnections and what ever I do I cannot get a connection back unless I restart.  I have asked for help on this forum but have only had one reply which suggested my router maybe at fault.  Thing is - my wifi has been rock solid since 10.04 and if I go onto winxp it is rock solid.  I have just reinstall 10.04 and i is happening again.  I like 10.04 but it looks like I may have to go back to 9.

---

### Post by coffeecat on 2010-09-15
Yes you can. Create a new partition for the 9.10 root and choose the manual option in the installer at the partitioning stage. Don't create another swap partition - one is enough for a Linux multiboot. And if you have a separate /home you'll need to deal with that in the manual partitioning stage. Unless you select the advanced option at the last screen of the installer, the 9.10 grub bootloader will be installed to the MBR, but that's OK because it will set up a multi-booting menu for you.

As far as the wi-fi is concerned, that sounds like a driver regression in Lucid. Do you know what chipset you have in the USB wireless nic?

**Edit:** if you want some help with the partitioning, post the terminal output of:

```
sudo fdisk -l
```

---

### Post by Quarkrad on 2010-09-15
I have a Sweex USB wireless stick - the chipset is Ralink RT2571WF.  According to Ubuntu the driver i is using to 'talk' to the USB device is rt73usb - this sounds about right to me (I am a newbie!) because winxp assigns RT73 drivers for this device.

---

### Post by coffeecat on 2010-09-15
> **Quarkrad said:**
> I have a Sweex USB wireless stick - the chipset is Ralink RT2571WF.  According to Ubuntu the driver i is using to 'talk' to the USB device is rt73usb

I couldn't find anything that matches your problem in Lucid 10.04. Two suggestions:

If you do a warm reboot from Windows, the firmware for some wireless NICs fails to load properly. However, this would normally result in no function at all rather than random disconnects, but it's worth excluding as a problem. Try a cold bootup into Ubuntu. The machine doesn't have to be physically cold, rather, power down completely from Windows, wait a little while and then boot into Ubuntu.

The other thing that might be worth trying is to install the backported wireless modules. These are drivers from a newer kernel than the one in Lucid, but compiled to work in Lucid. I've checked the package you'd install and it does include the rt73usb driver - so this might be a later version. Don't let anyone tell you that you need to enable the backports repository for this - you don't. The package you need is in the main repository. Simply install the linux-backports-modules-wireless-lucid-generic package in Synaptic. This is a metapackage which will pull in the package appropriate to your kernel and will make sure you get an update when the kernel is updated. I'm assuming you have the generic kernel. To check this, from the terminal, just do:

```
uname -r
```... and if you get "2.6.32-24-generic" as output you have the generic kernel. (Don't worry if the last number is different.) If you get anything other than 'generic', don't install that package and post back.

---

### Post by Quarkrad on 2010-09-15
Thank you very much for your help.  I am in a bit of a mess now - I cannot get a connection even if I reboot.  One thing I did note 'googling' was a thread that seemed to have an issue if, when using the command, lsusb, there was a line for Ralink that included the term 148f:2573.  Unfortunately the thread stopped.  If I run lsusb I get the line **bus 002 device 004: id 148f:2573 Ralink Technology, Corp.  RT25001USB wireless adpater.**  At the moment I have no connection - this is posted on lap top.

---

### Post by coffeecat on 2010-09-15
The chipset id, 148f:2573 in your case, is the important bit. The make and model of the NIC can be misleading - some manufacturers put different chipsets in the same model number at different times. I tried searching with that id string and came up with something which might help. See this post:

[http://ubuntuforums.org/showpost.php?p=9547145&postcount=9](http://ubuntuforums.org/showpost.php?p=9547145&postcount=9)

I've taken it out of its thread - it was the last post - because there were some irrelevant posts confusing the issue. It suggests that the rt73 driver you need is being blocked by one of the rt2*** drivers. Try that first line of code:

```
echo 'blacklist rt2500usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

... and then reboot. If it doesn't work, it's easily reversed. Any blacklist line in /etc/modprobe.d/blacklist.conf will prevent that driver from being loaded. So - worth a try. In the meantime, I'll see if I turn up anything else. Post back with what happens.

---

### Post by Quarkrad on 2010-09-15
I put the command in terminal and the response was **blacklist rt2500usb**.  I have rebooted and I have a connection - guess the test is to see if it holds up.  I will leave pc on and see if it holds up - will post later.  Thanks.

---

### Post by coffeecat on 2010-09-15
> **Quarkrad said:**
> I put the command in terminal and the response was **blacklist rt2500usb**.

That command will (should) have written a line to /etc/modprobe.d/blacklist.conf. If you want to double-check that it is there, simply:

```
cat /etc/modprobe.d/blacklist.conf
```... and the whole contents of the file will show in the terminal. There'll be a whole load of lines that the developers put in to deal with problematic modules, and the blacklist rt2500usb line should be at the very end.

I'll keep my fingers crossed for you. :)

---

### Post by quadproc on 2010-09-15
> **Quarkrad said:**
> I have a dual boot 10.04 and winxp system - can I install Ubuntu 9.10 as well?
As coffeecat said, yes, you can.  I am presently running a system with 8.10, 9.10, and 10.04 on my main disk.  In order to make this work correctly, each version is in its own partition.  And, to simplify my life, I have placed my /home on a separate disk drive in its own partition.  Both the 9.10 and 10.04 installations use the /home on that drive so the same data is available regardless of which of those two versions I boot.

It is possible to install an Ubuntu version "alongside" an existing version but when I tried this I ended up with a non usable version - little problems like no cursor being displayed.  So I suggest keeping each version in its own partition. Both grub and grub-pc work just fine with this arrangement.

quadproc

---

### Post by Quarkrad on 2010-09-16
Damn - it's still there (dis-connecting).  I had it running for a good 3 hours and it was rock solid (like the old days - Ubuntu 8/9) and this morning it was on or a good while.  Unfortunately this afternoon it dis-connected again. This time I'm using WCID - it scans for wireless networks and finds nothing.  Is it time to give up on his one - just put it down to a Ubuntu 10.04 'feature'.  Strange it was like a rock throughout versions of 8 and 9 but breaks in 10.04 - Ralink is a reasonable device/build.

---

### Post by coffeecat on 2010-09-16
Sorry that blacklisting the rt2500usb module didn't work.

Before you give up on Lucid, just a couple of things to try:

1 Try the other blacklist command from that single post I linked:

```
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```That will mean you've blacklisted both of the rt2*00usb modules. It won't do any harm, and may clear the field for the rt73usb.

2 If that doesn't help, try the backports package I mentioned a few posts ago. That will give you the rt73usb driver from 10.10/Maverick. Tbh I don't know whether it's any different but it's worth a go.

Apart from that, sorry, I have no further ideas.

**Except:**

Maybe the problem is not entirely with the Lucid rt73 driver. I know that Karmic and Windows were OK but it's still worth excluding other factors. For instance, what channel is your router transmitting on? Are neighbours using the same channel? You need some sniffer software to find out, but if you have crowded airwaves it's worth changing the channel of your router. Or simply, experiment with different channels. If on 6, try 1 or 11. If on 11, try 1, and so on. Also - it could be just coincidence that you're getting the problem with Lucid. Perhaps a neighbour started using a baby alarm (a well-known interferer of the wi-fi channels) just about the time you started with Lucid. Or a microwave.

Tbh, I've given up on wireless for my desktop machines. PCI cards have the antenna too near the motherboard and you can't move it into an ideal location. USB devices with short leads tend to be affected by the field from the monitor. And so on. So I use ethernet over mains for my desktop machines (+network printer +NAS +PS3) and it's much more reliable. Expensive, but "just works".

---

### Post by Quarkrad on 2010-09-16
Thanks.  I'll go one step at a time -just blacklisted the 280 driver.  Be back to let you know!

---

### Post by Quarkrad on 2010-09-30
No luck so far - I think I will have to give up on this one, must be some sort of odd 10.04 thing(?).  To save time rebooting I looked into ways of restarting the networking environment but so far no deal. I tried **sudo killall NetworkManager** - terminal gave me:


[B]dad@dadubuntu:~$ sudo killall NetworkManager
[sudo] password for dad: 
dad@dadubuntu:~$ sudo networkmanager
sudo: networkmanager: command not found
dad@dadubuntu:~$ sudo NetworkManager

** (NetworkManager:1790): WARNING **: NetworkManager is already running (pid 1787)[/B]

I then had a look in System/Admin/System Monitor/Processes for process ID 1787 but there was no process no. 1787.  If I left click network manager icon in the top panel there are no wireless devices listed. At one point I had WICD (I now have only gnome network manager) and when I restarted networking(with terminal commands) wicd just sat there scanning for wireless devices and again 'saw' nothing.  Looks like the only way I can get connection back is to reboot.

---

