---
title: "Cannot find ethernet device"
date: 2011-09-09
forum: General Help
---

### Post by Peter Robertson on 2011-09-09
I am a novice when it comes to Ubuntu (or any flavour of Unix).

I have a new 64-bit PC with Windows 7 and I can install several variants of Ubuntu (64-bit 10.04, 32-bit 11.04, etc) and they all work without problems. In particular, they all find the ethernet device eth0 and it works perfectly.

My problem is that I need to use tools that refuse to install on anything but Ubuntu 10.04 LTS 32-bit. I can install this and it works fine EXCEPT that it finds no ethernet device. As the installation of these tools needs to download things from the net, I am stuck. I have tried installing 10.04 several times as one post suggested, but this makes no difference.

I have tried to find solutions for this using google, but the best I can get are screeds of frankly unintelligible commands for specific ethernet devices.

There must be something basic going wrong, as lots of old and new versions of Ubuntu find my device without difficulty.

I would really appreciate some basic help on this.

---

### Post by Bodsda on 2011-09-09
> **Peter Robertson said:**
> I am a novice when it comes to Ubuntu (or any flavour of Unix).
 
I have a new 64-bit PC with Windows 7 and I can install several variants of Ubuntu (64-bit 10.04, 32-bit 11.04, etc) and they all work without problems. In particular, they all find the ethernet device eth0 and it works perfectly.
 
My problem is that I need to use tools that refuse to install on anything but Ubuntu 10.04 LTS 32-bit. I can install this and it works fine EXCEPT that it finds no ethernet device. As the installation of these tools needs to download things from the net, I am stuck. I have tried installing 10.04 several times as one post suggested, but this makes no difference.
 
I have tried to find solutions for this using google, but the best I can get are screeds of frankly unintelligible commands for specific ethernet devices.
 
There must be something basic going wrong, as lots of old and new versions of Ubuntu find my device without difficulty.
 
I would really appreciate some basic help on this.
 
What tools are refusing to install? Can you provide error messages.
What is the current state of your system, what version and do you currently see eth0?
 
Thanks,
Bodsda

---

### Post by Peter Robertson on 2011-09-09
The tools I am trying to install are from Texas Instruments, but they are actually a side issue. The real problem, as I described, is that there is no ethernet device detected.

I currently have Ubuntu 10.04 LTS (32-bit) installed, as I said previously.

There are no error messages, but no ethernet device is found (no eth0).

---

### Post by Bodsda on 2011-09-09
> **Peter Robertson said:**
> The tools I am trying to install are from Texas Instruments, but they are actually a side issue. The real problem, as I described, is that there is no ethernet device detected.
 
I currently have Ubuntu 10.04 LTS (32-bit) installed, as I said previously.
 
There are no error messages, but no ethernet device is found (no eth0).
 
Please paste the output of the following commands
 
```

ifconfig

```
 
```

lspci

```
 
Thanks,
Bodsda

---

### Post by Peter Robertson on 2011-09-09
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12400 (12.4 KB)  TX bytes:12400 (12.4 KB)


lspci
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 05)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c4a (rev 05)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6759
01:00.1 Audio device: ATI Technologies Inc Device aa90
03:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)

---

### Post by Bodsda on 2011-09-09
> **Peter Robertson said:**
> ifconfig
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:164 errors:0 dropped:0 overruns:0 frame:0
TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:12400 (12.4 KB) TX bytes:12400 (12.4 KB)
 
 
lspci
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 05)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c4a (rev 05)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6759
01:00.1 Audio device: ATI Technologies Inc Device aa90
03:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
 
And just to be sure, you have a network cable plugged into the ethernet card, and then into the correct port on the router, yes?
 
Bodsda

---

### Post by Peter Robertson on 2011-09-09
As I stated in my original post, I have had other versions of Ubuntu installed on this PC and running correctly WITH internet access.

Windows 7 is also installed on the PC and if I start that, I can access the internet without problems.

Starting Ubuntu 10.04 without changing anything else makes the ethernet card disappear.

---

### Post by Bodsda on 2011-09-09
> **Peter Robertson said:**
> As I stated in my original post, I have had other versions of Ubuntu installed on this PC and running correctly WITH internet access.
 
Windows 7 is also installed on the PC and if I start that, I can access the internet without problems.
 
Starting Ubuntu 10.04 without changing anything else makes the ethernet card disappear.
 
Well, as detailed in output from lspci, the card has not disappeared, it is recognized. 
 
According to this forum - [http://forums.fedoraforum.org/showthread.php?t=257676](http://forums.fedoraforum.org/showthread.php?t=257676)
the driver is available in the 2.6.36 kernel.
 
What kernel version do you have?
 
Thanks,
Bodsda

---

### Post by gandaran on 2011-09-09
> I have a new 64-bit PC with Windows 7 and I can install several variants of Ubuntu (64-bit 10.04, 32-bit 11.04, etc) and they all work without problems. In particular, they all find the ethernet device eth0 and it works perfectly.
well you did say here ethernet worked on 10.04.
> 00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 05)
if it doesn't really work then this ethernet card is not supported on 10.04, you may have to install drivers.

---

### Post by Peter Robertson on 2011-09-09
I said previously that it works with **64-bit** 10.04; it does not work with 32-bit 10.04.

Perhaps my terminology was incorrect when I said the Ethernet card had 'disappeared'. I meant by that that the device eth0 had disappeared from the list of devices shown by ifconfig.

How do I determine which version of hte kernel I am running?

---

### Post by Bodsda on 2011-09-09
> **Peter Robertson said:**
> I said previously that it works with **64-bit** 10.04; it does not work with 32-bit 10.04.
 
Perhaps my terminology was incorrect when I said the Ethernet card had 'disappeared'. I meant by that that the device eth0 had disappeared from the list of devices shown by ifconfig.
 
How do I determine which version of hte kernel I am running?
 
Try 
```

uname -r

```
 
Bodsda

---

### Post by Peter Robertson on 2011-09-09
2.6.32-33-generic

---

### Post by Bodsda on 2011-09-09
> **Peter Robertson said:**
> 2.6.32-33-generic
 
According to that fedora forum, your kernel does not include the drivers for that network card. 
 
Bodsda

---

### Post by Peter Robertson on 2011-09-09
Can you point me at somewhere that describes locating and installing drivers that does not assume I am a Linux expert?

---

### Post by tredegar on 2011-09-09
It looks to me as though your Intel ethernet device needs the module **e1000e** to be loaded. This module is available to the ubuntu 2.6.32-33-generic kernel.

If it is already loaded it will be listed with the command
```
lsmod | grep e1000e
```
If it is not listed by that command, load it with
```
sudo modprobe e1000e
```
Then see if **eth0** is listed by
```
ifconfig
```
If it is, you should be set to go.

---

### Post by Peter Robertson on 2011-09-09
Thank you for the suggestion.

I executed the lsmod command and it displayed nothing.

I then executed the sudo modprobe e1000e command. It asked for my password then returned to the command prompt without any further output.

ifconfig still shows only 'lo'; there is no 'eth0'.

I then repeated the lsmod command and it printed:
e1000e   119888 0
With the e1000e in red.

:-(

---

### Post by tredegar on 2011-09-09
> I executed the lsmod command and it displayed nothing.
- which means the module was not loaded.
> I then executed the sudo modprobe e1000e command. It asked for my password then returned to the command prompt without any further output.
- which means the module was loaded.
> ifconfig still shows only 'lo'; there is no 'eth0'.
- bad news, because with the module loaded, the device *should* appear as **eth0**
> I then repeated the lsmod command and it printed:
e1000e 119888 0
With the e1000e in red.
In red? Never seen that before, but it probably means something bad.

If you are dual-booting this box with windows, remember win can sometimes leave hardware in an odd state, so linux cannot "see" it (as in your current situation).

Try powering it _right_ down (no power cord, and no battery if a laptop), then reboot to ubuntu 10.04 then try the commands I gave you again. Do not boot to windows after the power-down until you have tried linux from a cold boot.

---

### Post by Peter Robertson on 2011-09-09
I tried again after powering-down and removing the power cord for a minute.
I get exactly the same behaviour.

---

### Post by tredegar on 2011-09-09
OK.
Try booting to a version of linux that does see eth0 (anything but 10.04 32-bit, it seems).
Then tell us the output of
```
sudo ethtool -i eth0
```

---

### Post by Peter Robertson on 2011-09-09
I have removed the 32-bit 10.40 system and installed the 64-bit version
(2.6.38-8-generic)

The eth0 device is found and I can access the internet.



The command:

sudo ethtool -i eth0
asks for my password then fails:
sudo: ethtool: command not found

---

### Post by tredegar on 2011-09-09
Ok
```
sudo apt-get install ethtool
sudo ethtool -i eth0
```
:)

---

### Post by Peter Robertson on 2011-09-09
driver: e1000e
version: 1.2.20-k2
firmware-version: 0.13-4
bus-info: 0000:00:19.0

---

### Post by tredegar on 2011-09-09
Thank you.
I've been doing a bit of searching.

Looks like e1000e is broken on 10.04 kernel 2.6.32-*

The following is going to be *fun*, and will get your eth0 working.

Take a deep breath, and stay calm.

You need to get the driver ("module") source code from here:
e1000e-1.5.1.tar.gz
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3003&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3003&lang=eng)

Download it **e1000e-1.5.1.tar.gz** to your **~/Downloads** folder.

Become root, get the stuff you need to compile things,  untar it, then compile it, install it and load it:
```
sudo -i
apt-get update
apt-get install build-essential
modprobe -r e1000e # remove it (if it was loaded)
cd /home/peter/Downloads
tar xfz e1000e-1.5.1.tar.gz 
cd e1000e-1.5.1/src
make install
modprobe e1000e
exit
ifconfig
```

You can copy & paste those commands (safest).

If you update the kernel, you'll need to do:
```
sudo -i
modprobe -r e1000e # remove it (if it was loaded)
cd /home/peter/Downloads/e1000e-1.5.1/src
make install
modprobe e1000e
exit
ifconfig
exit
```

Let us know how you get on.

---

### Post by Peter Robertson on 2011-09-09
Before I start, which version of Ubuntu should I have installed when I do what you suggest?

I am also concerned when you write 'If you update the kernel, you'll need to do'

'If you update the kernel': I have no idea how I decide if I need to do that or how.

---

### Post by tredegar on 2011-09-09
> Before I start, which version of Ubuntu should I have installed when I do what you suggest?
The version it seems you want/need is 10.04LTS 32-bit (and just happens to be what I am running).

This seems to be the only version with a broken e1000e module.

This is the version that needs to be running when you compile e1000e from source.

I realise that if **eth0** is not working with 10.04LTS, you may have trouble installing **build-essential**. Perhaps you can buy/borrow a USB wireless device (to connect to your wireless router, or even a 3G mobile phone type dongle), or plug in PCI ethernet port with a chipset that *is* working with 10.04LTS, so the machine can access the internet to D/L the software you need.

> 'If you update the kernel': I have no idea how I decide if I need to do that or how.
Every now and again 10.04 tells me there are updates available, and I install them. Eg, yesterday there was an update to firefox to blacklist that company (DigiNotar) that has had its "secure certificates" compromised. Sometimes there's also a  kernel update eg 2.6.32-32-generic -> 2.6.32-3[COLOR="Red"]3[/COLOR]-generic 

Kernel updates are a good idea - they improve security and fix things ( but your e1000e module isn't fixed yet, you could file a bug report).

Take a look at System - Administration - Update Manager.

---

### Post by Peter Robertson on 2011-09-09
I have restored 10.04 and, of course, the ethernet is still absent.
I have a USB wireless card that is visible in iwconfig as wlan0, but it is
not set up as a network connection.

I have looked on the web and found a description of how to set it up, but
I see references to System-Administration-Network and Network Manager.
There is no System-Administration-Network entry. The closest is Network Tools.

How do I set up the wireless so I can do the installation you suggested?

---

### Post by tredegar on 2011-09-09
> I have a USB wireless card that is visible in iwconfig as wlan0, but it is
not set up as a network connection.
Good, but you need to set it up.
> How do I set up the wireless so I can do the installation you suggested?
You use Network Manager [which should be on your panel (at the top)]  clicky-clicky.

If not, and you can't find NM any other way (Eg R-click a blank bit of the panel, Add to panel, Network Manager), you can put this into the file **/etc/network/interfaces** with the command
```
gksudo gedit /etc/network/interfaces
```
Make it look like this (If you are not using encryption, or it is not WPA, then it should be):
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-passphrase [COLOR="Red"]yourpassphrase[/COLOR]
wpa-ssid [COLOR="Red"]yourssid[/COLOR]
wireless-channel [COLOR="Red"]11[/COLOR]
```
The [COLOR="Red"]red[/COLOR] bits need to be changed to suit your setup.
Save the file. Then:
```
sudo /etc/init.d/networking restart
```

You should be connected, and will again be, wirelessly, at the next reboot.

---

### Post by Peter Robertson on 2011-09-09
I have tried this and the final restart command comes up with :
No DHCPOFFERS received
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory

I can connect to the wireless using a Windows laptop, so I know it is working.

Any suggestions?

---

### Post by Peter Robertson on 2011-09-09
P.s. I had to edit the interfaces file manually.; I could not find Network Manager anywhere. It was not in the Add to panel list.

Also, in case it's relevant, the Wireless router mode is set to WPA2/PSK.

---

### Post by gandaran on 2011-09-09
> **Peter Robertson said:**
> I have tried this and the final restart command comes up with :
No DHCPOFFERS received
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory

I can connect to the wireless using a Windows laptop, so I know it is working.

Any suggestions?
maybe the wireless adapter isn't supported too, need drivers 
type in terminal
```
lsusb
```
to find the wireless chipset brand

---

### Post by gandaran on 2011-09-09
> **Peter Robertson said:**
> P.s. I had to edit the interfaces file manually.; I could not find Network Manager anywhere. It was not in the Add to panel list.

Also, in case it's relevant, the Wireless router mode is set to WPA2/PSK.
in the add to panel list it's the 'notification area' applet that provides the network manager icon.

---

### Post by Peter Robertson on 2011-09-10
Adding the Notification Area just adds another inactive icon with three small horizontal lines; I assume this is a separator. There is already one followed by an icon with a red exclamation mark (containing Enable Networking,...), then a volume control, an envelope, date, time, a speech balloon with an X and login name, then the off switch. None of them says anything about Network Manager. Do you mean the icon with the exclamation mark?
It has Edit Connections, but that comes up with no entries and no obvious way to enter the information required.

lsusb finds the wireless device: ID 0df6:003f Sitecom Europe B.V.

When it is inserted, ifconfig shows two entries: wlan0 and wlan0:avahi

---

### Post by gandaran on 2011-09-10
> There is already one followed by an icon with a red exclamation mark 
none of your internet devices are working so network manager probably won't work too.
> lsusb finds the wireless device: ID 0df6:003f Sitecom Europe B.V.
well Ubuntu failed to identify the chipset, this is new hardware and needs a driver, can you find out the wireless chipset brand in the windows system hardware?

---

### Post by Peter Robertson on 2011-09-10
How about looking at this the other way round. Is there a commonly-available USB Wireless adaptor that is KNOWN to work with 10.04 without having to download anything?

Also, is it possible to download things that need to be installed without actually installing them? I could download the necessary files from a working PC, transfer them across and install without needing a working internet connection.

---

### Post by gandaran on 2011-09-10
> Is there a commonly-available USB Wireless adaptor that is KNOWN to work with 10.04 without having to download anything?
there are still some available but most are new hardware and won't work on 10.04 out of the box, some chipset manufactures provide linux drivers you just have to know the chipset model and brand to download the driver.
> Also, is it possible to download things that need to be installed without actually installing them? I could download the necessary files from a working PC, transfer them across and install without needing a working internet connection.
you can get every package from [Ubuntu packages]("http://packages.ubuntu.com/"), download the .deb file and click to install

also I believe you can run the 32-bits applications on 64-bits Ubuntu, you just need to install some 32-bits libs packages to run 32-bits applications

---

### Post by tredegar on 2011-09-10
> **gandaran said:**
> none of your internet devices are working so network manager probably won't work too.

well Ubuntu failed to identify the chipset, this is new hardware and needs a driver, can you find out the wireless chipset brand in the windows system hardware?
His chipset _is_ supported ( because, earlier, he said the device **wlan0** is created ). The USB device 0df6:003f uses the **rt2800usb** module.

> It has Edit Connections, but that comes up with no entries and no obvious way to enter the information required.
You can _either_ use Network Manager _or_ edit **/etc/network/interfaces**. Not both. Interfaces listed in that file will be ignored by NM.

If you'd rather use the NM GUI, then edit **/etc/network/interfaces** to look like this:
```
auto lo
iface lo inet loopback
```
Then restart networking (or reboot), then try to use the NM GUI to connect you.

> How about looking at this the other way round. Is there a commonly-available USB Wireless adaptor that is KNOWN to work with 10.04 without having to download anything?
Your device works, but it needs to be configured with the details of your network.
> Also, is it possible to download things that need to be installed without actually installing them? I could download the necessary files from a working PC, transfer them across and install without needing a working internet connection. 
This is possible, but it is complicated, because it's not just one file you need but many, because of "dependencies". And you'll need to download the files whilst running 10.04 or the wrong versions will be fetched.

I suggest you concentrate of getting wireless working: Edit that file, to remove all references to **wlan0** and then use NM.

---

### Post by Peter Robertson on 2011-09-10
That sounds like the way forward. The question now is, which of the many packages do I need to download and install?

---

### Post by tredegar on 2011-09-10
Did you miss my post at #36?
Get wireless working.

---

### Post by gandaran on 2011-09-10
check this guide
[http://johnsunixtips.blogspot.com/2010/08/sitecom-wireless-wl-608-54g-usb-dongle.html](http://johnsunixtips.blogspot.com/2010/08/sitecom-wireless-wl-608-54g-usb-dongle.html)

---

### Post by Peter Robertson on 2011-09-10
This site is very slow. It can take 5 minutes to refresh. You post #36 had not come through when I made my post.

---

### Post by tredegar on 2011-09-10
> **gandaran said:**
> check this guide
[http://johnsunixtips.blogspot.com/2010/08/sitecom-wireless-wl-608-54g-usb-dongle.html](http://johnsunixtips.blogspot.com/2010/08/sitecom-wireless-wl-608-54g-usb-dongle.html)
No. 

This is _not needed_ because **wlan0** has been created. This means that the wireless interface is recognised and _working_, but it still needs the details of his network to establish a connection.

---

### Post by Peter Robertson on 2011-09-10
I have undone the suggestion from #27, so now /etc/network/interfaces contains only this:

auto lo
iface lo inet loopback

Now I am back to the problem of finding this Network Manager. I have tried every control I can see and not one has an entry called "Network Manager". Is this a general term for something that actually has a different name?

I tried the suggestion from the referenced site "Unix Tips":

** lsmod | grep rt**

**$ sudo rmmod rt2800usb && sudo rmmod rt2x00usb && sudo rmmod rt2x00lib**

[B]$ sudo modprobe rt2870sta

[/B]This had no effect, even after removing and re-inserting the dongle..

---

### Post by gandaran on 2011-09-10
> Now I am back to the problem of finding this Network Manager. I have tried every control I can see and not one has an entry called "Network Manager". Is this a general term for something that actually has a different name?
system » preferences » network, opens the same network manager window as in clicking the panel network icon » edit connections.

---

### Post by Peter Robertson on 2011-09-10
When I click system >> preferences I get:

...
Mouse
Network Connections
Network Proxy
Personal File Sharing
...

There is no entry "Network".

---

### Post by gandaran on 2011-09-10
> **Peter Robertson said:**
> When I click system >> preferences I get:

...
Mouse
Network Connections
Network Proxy
Personal File Sharing
...

There is no entry "Network".

Network Connections » wireless tab » add » setup the connection details, you just have to enter the ssid network name then click the network icon and choose your network to connect.

---

### Post by Peter Robertson on 2011-09-10
Clicking Edit Connections... bring up a Network Connections window that contains nothing under the Wired or Wireless tabs.

---

### Post by gandaran on 2011-09-10
> I tried the suggestion from the referenced site "Unix Tips":

lsmod | grep rt

$ sudo rmmod rt2800usb && sudo rmmod rt2x00usb && sudo rmmod rt2x00lib

$ sudo modprobe rt2870sta

This had no effect, even after removing and re-inserting the dongle..
just keep trying, in my experience sometimes things don't just work the first time in Linux or try **tredegar** way
and you probably need to reboot after modifying etc/network/interfaces before you can run those commands.

---

### Post by Peter Robertson on 2011-09-10
Using the Network Conneections window I have configured the wireless settings for wlan0 (based on the settings from a Windows laptop that can connect to the router).

SIID: <set appropriately>
Mode: Infrastructure
BSSID: 
Mac addresss: <the MAC address of wlan0 from ifconfig>
MTU: automatic

Wireless security
Security: WPA & WPA2 Personal
Password ........

IPv4 Settings
Method: Automatic (DHCP)
DHCP client ID:
Available to all users (ticked)

Connect automatically (ticked)

I have rebooted and nothing has really changed. In Wireless connections I now have "Wireless connection 1" Last used: never.

Is there anything else I need to do to get the wireless to work?

---

### Post by gandaran on 2011-09-10
> I have rebooted and nothing has really changed. In Wireless connections I now have "Wireless connection 1" Last used: never.
rebooted? you have loaded the rt2870sta driver permanently?
if you haven't then run all those commands again to temporally load the driver.

---

### Post by Peter Robertson on 2011-09-10
re #47: repeating the rmmod commands gives an error now: Module rt2x00lib is in use by rt2800use, rt2x00usb

---

### Post by Peter Robertson on 2011-09-10
That should have been: Module rt2x00lib is in use by rt2800usb, rt2x00usb

---

### Post by gandaran on 2011-09-10
> **Peter Robertson said:**
> re #47: repeating the rmmod commands gives an error now: Module rt2x00lib is in use by rt2800use, rt2x00usb
sorry cannot help with this but try repeating the command.
you can check which ralink drivers/modules are loaded typing in terminal
```
lsmod
``` 
they begin with [COLOR="DarkRed"]rt[/COLOR]

---

### Post by Peter Robertson on 2011-09-10
Device - Network Tools has only Loopback interface (lo) under Network device.

I have tried repeating the rmmod & modprobe commands several times. Nothing changes.

---

### Post by Peter Robertson on 2011-09-10
To clarify: the rt2870sta driver is shown in the lsmod output, but wireless is still not appearing in the list of network devices under Device - Network Tools.

---

### Post by Peter Robertson on 2011-09-10
I have managed to get the wireless to work.

For future reference this is what I did:

1: remove the wireless dongle
2: reboot the PC
3: give the command: sudo modprobe rt2870sta
4: insert hte wireless dongle
5: wait

No I shall try the suggestion to get the wired connection to work.

---

### Post by Peter Robertson on 2011-09-10
I have now followed the instructions in #23 and have managed to get the wired internet connection to work.

A huge thank you to all who have helped me.

---

### Post by gandaran on 2011-09-10
> **Peter Robertson said:**
> I have managed to get the wireless to work.

For future reference this is what I did:

1: remove the wireless dongle
2: reboot the PC
3: give the command: sudo modprobe rt2870sta
4: insert hte wireless dongle
5: wait

No I shall try the suggestion to get the wired connection to work.
congratulations :D 
just like I said you have to keep trying if it doesn't work fist time.

---

### Post by tredegar on 2011-09-10
> I have now followed the instructions in #23 and have managed to get the wired internet connection to work.
Congratulations.
Don't forget to bookmark #23 - you'll need it when the kernel is next updated.

---

### Post by Peter Robertson on 2011-09-10
Actually, it wasn't a case of repeating things. The solution was to discover the EXACT steps needed and the order in which to perform them.

I can't help but think that there is far too much magic involved.

---

### Post by gandaran on 2011-09-10
> **Peter Robertson said:**
> Actually, it wasn't a case of repeating things. The solution was to discover the EXACT steps needed and the order in which to perform them.

I can't help but think that there is far too much magic involved.
no magic at all :D my experience with Linux is to keep trying and sometimes with different approaches, you may find a guide for a particular Ubuntu release but on your actual Ubuntu release you may have to do something different to get results.

---

