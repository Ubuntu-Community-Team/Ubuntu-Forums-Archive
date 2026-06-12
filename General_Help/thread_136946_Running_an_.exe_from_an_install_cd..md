---
title: "Running an .exe from an install cd."
date: 2006-02-27
forum: General Help
---

### Post by metacoola on 2006-02-27
I have just recently gotten linux so I really am trying hard to learn. So I am trying to get my wireless adapter to work on it, but I first know it should at least have the power installed first, It is a 2wire wireless usb adapter and it works fine on winXP(dual boot) I have an install cd(it came with the usb adapter((sbcyahoo!)) ), but it doesn't auto run, so I see a setup.exe type file and when I double click it, nothing happens, so which program or app should I choose to run it, or how else can I open the .exe

---

### Post by monolegis on 2006-02-27
You can not open exe files in linux. Exe files are windows filetypes. 

You may be able to run the files with wine, but then again I don't think the result would be any good.

---

### Post by metacoola on 2006-02-27
So does anyone know If I can get an installer working on linux, or how I can get the wireless adapter in general working? Because the main reason I use windows instead of ubuntu is because ubuntu doesn't have any internet functionality for me right now.

---

### Post by monolegis on 2006-02-27
I have never used wireless, but I think it would help if you posted which model you are using (modem/router/wireless adapter). Maybe it exists linux drivers for it, or maybe ndiswraper is a solution, but then again I wouldn't have any clue.

---

### Post by ltmon on 2006-02-27
Hi Metacoola,

You might have more luck posting in the "networking" forum.  That's where most of the people with good wireless knowledge look.  You will need to post some specifics on your model for anyone to be able to help you though.

You should also have a look at this wiki page.  If your wireless adapter is listed on it you will get more information: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by FeestBijtje on 2006-02-27
Most times when i got problems i use google to find it ;)
Good tip: use "Ubuntu How to <install/Add/remove/use> <problem/question/device>"
That helps me out for the most things

---

### Post by Madpilot on 2006-02-27
For NDISWrapper - wireless on Linux using Windows drivers - have a look here:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

---

### Post by metacoola on 2006-02-27
I tried entering 1spci -v | less but nothing happened, the terminal went blank with the word end at the bottom, and I can't find my router at any of the compatability charts. maybe i am typing to command line wrong?

---

### Post by taurus on 2006-02-27
That should be lspci -v | less, NOT 1spci -v | less!!!

---

### Post by metacoola on 2006-02-27
So wait, are is the sign before the spci a bar sigh or an "I" and same for the second bar. Because I did |spci -v | less (both bars) and I got the same thing.

---

### Post by shamrock_uk on 2006-02-27
It's an 'ell' as in 'love'.  The command is short for 'listpci'

---

### Post by metacoola on 2006-02-27
Okay, thank you for that, I got it now, although heres what it says on the bottom.
[SIZE="2"]0000:02:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/ Prism Xbow] (rev 01)
 Subsystem: Unknoown device 1630:0003
 Flags: bus master, medium devsel, latency 80, IRQ 11
 Memory at 108000000 (32-bit, non-prefetchable)  [size=8k]
 Capabilities:  [dc] Power Management version 2[/SIZE]

Is anyone able to help me with this? Thanks

---

### Post by shamrock_uk on 2006-02-27
I believe this will do the trick, courtesy of [http://www.ioi.knaw.nl/~heimel/computers/connecting_wireless](http://www.ioi.knaw.nl/~heimel/computers/connecting_wireless)

Just an FYI - the .exe file is simply the installer programme, not the drivers themselves. The walkthrough below uses ndiswrapper, a rather nifty programme that takes the .inf file from your drivers cd and is able to use them under linux.

You may need a walk through that, but I'm afraid I must be off. No doubt someone else can pick it up. 

I have seen references to this card being detected as eth0 automatically, without installing ndiswrapper so it may be worth telling us if you see anything when you go to system -> administration -> networking before you dive into the instructions below.

Good luck. 

> How to connect Prism Javelin/Xbow ISL3886 wireless chipset under linux (Fedora Core 4) on Cybermaxx Medion 

I took the following steps to connect the Prism Javelin/Xbow ISL3886 wireless chipset that was present in my Cybermaxx Median Athlon 3000+XP notebook under Fedora Core 4 GNU/Linux. Actually, I had to do very little. I used NdisWrapper. At the website [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) the necessary steps were explained quite clearly. Thanks to all who developed NdisWrapper! 
First I checked for the chipsets presence:
$ lspci

This shows controller among other things:
  00:0c.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)


~departure from website instructions~

just do:

```
$sudo apt-get install ndiswrapper-utils 
```

to install ndiswrapper.

~end simplification~

Not entirely sure whether this little section is necessary either. I would try skipping it first: 
```

$ lspci
  line of Prism Javelin network controller starts with 00:0c.0
$ lspci -n 
  00:0c.0 Class 0280: 1260:3886 (rev 01)

# so PCI ID is 1260:3886 (rev 01)
#  two drivers in list found
#  downloaded exe file from Medion

$ unzip wlansim2000g60xwinxp.exe 
```

This should do the trick:

```
$ ndiswrapper -i PRISMA00.inf
    Installing prisma00

$ ndiswrapper -l
Installed ndis drivers:
prisma00        driver present, hardware present

$ modprobe ndiswrapper
$ dmesg
ndiswrapper version 1.2 loaded (preempt=no,smp=no)

turned on wireless device using function keys

$iwconfig
wlan0     IEEE 802.11g  ESSID:off/any

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

$iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0C:F6:03:04:16
                    ESSID:"Sitecom"
$iwconfig wlan0 mode Managed
$iwconfig wlan0 key restricted xxxxx
$iwconfig wlan0 essid "Sitecom"
$iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"Sitecom"
$dhclient wlan0

#SUCCESS!

$ndiswrapper -m
# which made an alias for wlan0 in /etc/modprobe.conf


#changed /etc/sysconf/hwconf with 
driver: ndiswrapper
device: wlan0

#added in /etc/sysconfig/network-scripts/
ifcfg-wlan0:

DEVICE=wlan0
MODE=managed
ESSID="Sitecom"
KEY=xxxxx
BOOTPROTO=dhcp
HWADDR=00:30:B4:00:00:00
ONBOOT=no
TYPE=Ethernet
DHCP_HOSTNAME=XXXXXXX


# connecting doesn't happen yet at startup, but can
# be done by
$ ifup wlan0
```

---

### Post by veraction on 2006-02-27
This solution is probably too simple, but for my laptop all I had to do after installing Ubuntu was:

System -> Administration -> Networking
Then I saw an item, "Wireless Connection: Not configured", so I clicked on it then click "Properties", then configure (with DHCP) & make sure a wireless access point is selected

Then it worked.

Like I said, it won't be this easy if a driver couldn't be found or whatever

---

### Post by metacoola on 2006-02-28
Wow, thanks a lot for the guide, although its a bit overwhelming for me, considering I have never really used the terminal before. I try to things like install the Prisma00.inf, but it says its already installed, and when I try to remove it with -e, it says its not installed. So the rest of the things fall apart. Also, for the part with the lan0, I had a list and the main one it showed was eth0, but I don't know how to use the rest, since it wasn't working anyways. Is there a non terminal guide to this? :X Although it really is a good guide :)

---

### Post by shamrock_uk on 2006-02-28
To be honest, the console is the best place to do this because it gives nice helpful error messages and it's also much easier for you to just paste the commands I give you than me trying to explain how to do it graphically. I'll respond as I can today. 

Firstly, just run *iwconfig* from a terminal and check that you only get an entry titled *lo*. If you see eth0, ath0 or anything like that, then probably all you have to do is go to the networking preferences and use the gui. 



OK, assuming it isn't detected automatically you need to copy the .inf file to your hard drive somewhere. Don't forget to use the <tab> key to autocomplete addresses as you type to make things easier. 

Also, remember that Linux is *case-sensitive*. In other words, not Prisma00.inf but prisma00.inf

Copy the .inf file to your home folder either by dragging and dropping as you normally would OR using the following command in the terminal  (Applications -> Accessories -> Terminal):

```
cp /media/cdrom0/<insert directory here>/prisma00.inf ~
```

The next bit you really need a console for (incidentally, terminal and console are the same thing more or less - I just mean the terminal in gnome):

You need to get ndiswrapper to install that .inf file. Issue this command (you can copy and paste it in if necessary: ctrl+v won't work, so use the edit menu)

```
sudo ndiswrapper -i prisma00.inf
```

(you may need to enter your password, just go ahead). 

Please post the output of any errors here (highlight the text, right-click on it and choose copy).

If that worked then do the following:

```
sudo modprobe ndiswrapper
```

And again, post any error messages here please. This last step just loads ndiswrapper (complete with your driver).

Assuming that worked, then when you run the *iwconfig* command, you should see your card listed.

Now you can actually ignore the rest of the walkthrough above and switch back to the gui if you're more comfortable. 

Going to System->Administration -> Networking should reveal an unconfigured card now. You should be able to select it and go to 'properties' to configure it.

If that worked, then your final step is to get it to work automatically every time you turn on your computer. Switch back to the console and do the following:

```
sudo gedit /etc/modules
```

And then add *ndiswrapper* to the file, so it looks something like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
ndiswrapper
```

---

### Post by metacoola on 2006-02-28
Well, when I did the iwconfig, I got "lo" and it said no wireless connections, then I had eth0 and it says NOT READY! along with all these other things. And lastly there is sit0, which says the same as lo. So does that mean anything? Also, when I go to networking my card is already shown there, and I try configuring it with the static IP and everything, but the power is off. So I think that may be the problem, once I can get it to turn on, I can get the pci card to connect.

---

### Post by metacoola on 2006-02-28
ON a different note, do I go to the root terminal or jsut the normal terminal?

---

### Post by metacoola on 2006-03-01
[QUOTE=shamrock_uk]To be honest, the console is the best place to do this because it gives nice helpful error messages and it's also much easier for you to just paste the commands I give you than me trying to explain how to do it graphically. I'll respond as I can today. 

Firstly, just run *iwconfig* from a terminal and check that you only get an entry titled *lo*. If you see eth0, ath0 or anything like that, then probably all you have to do is go to the networking preferences and use the gui. [COLOR="Lime"]I see eth0 and something else[/COLOR]



OK, assuming it isn't detected automatically you need to copy the .inf file to your hard drive somewhere. Don't forget to use the <tab> key to autocomplete addresses as you type to make things easier. 

Also, remember that Linux is *case-sensitive*. In other words, not Prisma00.inf but prisma00.inf

Copy the .inf file to your home folder either by dragging and dropping as you normally would OR using the following command in the terminal  (Applications -> Accessories -> Terminal):
[COLOR="Lime"][/COLOR]
```
cp /media/cdrom0/<insert directory here>/prisma00.inf ~
```
[COLOR="Lime"][COLOR="Lime"][/COLOR][/COLOR]
The next bit you really need a console for (incidentally, terminal and console are the same thing more or less - I just mean the terminal in gnome):

You need to get ndiswrapper to install that .inf file. Issue this command (you can copy and paste it in if necessary: ctrl+v won't work, so use the edit menu)
[COLOR="Blue"]I tried searching the untarred file of ndiswrapper-1.10 for the Prisma00.inf and I couldn't find it, and when I type the code in, I get that it is already installed.[/COLOR]
```
sudo ndiswrapper -i prisma00.inf
```

(you may need to enter your password, just go ahead). 

Please post the output of any errors here (highlight the text, right-click on it and choose copy).

If that worked then do the following:

```
sudo modprobe ndiswrapper
```

And again, post any error messages here please. This last step just loads ndiswrapper (complete with your driver)[COLOR="Red"]I got the following FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted[/COLOR].

Assuming that worked, then when you run the *iwconfig* command, you should see your card listed.

Now you can actually ignore the rest of the walkthrough above and switch back to the gui if you're more comfortable. 
[COLOR="Red"]I'm actually trying to use the desktop with the wireless adapter right now(its not a pci card but it runs through usb,I'm typing using XP on the laptop. it gave me lo eth0 and sit0 [/COLOR]
Going to System->Administration -> Networking should reveal an unconfigured card now. You should be able to select it and go to 'properties' to configure it.[COLOR="Red"]The card was already visible for both computers, and was labeled eth0, I can activate it, but nothing happens.[/COLOR]

If that worked, then your final step is to get it to work automatically every time you turn on your computer. Switch back to the console and do the following:

```
sudo gedit /etc/modules
```

And then add *ndiswrapper* to the file, so it looks something like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
ndiswrapper
```[/QUOTE]
[COLOR="Lime"]Sorry for Triple posting, but I really want this thread to continue because I am sort of lost..Sorry.[/COLOR]

---

### Post by shamrock_uk on 2006-03-02
Sorry, I'm a little tied up today. Will try and get back to you properly by tomorrow. 

The normal terminal is fine. The command 'sudo' which precedes all the commands I wrote down for you allows you to run those individual programmes as root. It's just a little safer than running around with a root terminal.

You'll have to be a little more specific with regards your errors in the Gnome network manager. What do you mean when you say you try and configure but the power is off? What is the exact error message? 

I'm assuming it's plugged in by the way if it needs to be...

There is a way to configure it manually but I forget the exact syntax. In your /etc/network/interfaces file you can basically add an entry something like this:

```
iface eth0 inet dhcp
``` along with a couple of other things. I forget the exact format, but you could probably search for a couple of those commands to see a complete one or I'll dig it out for you later from my own. 

It's probably better to get to the bottom of your errors in Gnome network manager though so please post precisely what happens and what messages you get. 

ie. "I click on the properties button, then I immediately get an error saying xxxxx"

Don't worry, we'll get it working ;)

---

### Post by metacoola on 2006-03-02
Thanks for all of that, to be more specific, I guess I should give more backround info. I have a desktop and a laptop with winXP and dual boot linux. One has a 2wire pci card, the other has a wireless usb adapter. Originally, the Prisma/xbow is the pci card, then I tried running on the terminal on the desktop one, so it was kind of getting all confused. The reason I bring up the power, was because in XP, I couldn't get it to work, because I had to go to the device manager and then the power light(the other light is for the actual connection) on the pci card, lighted up, then I could work on the network. The same happened with the wireless usb adapter. So I'm thinking, before I get the network connection working, there maybe a device recognition error.  Like it doesn't allow it to get power or something. Sorry if this is too vague

---

