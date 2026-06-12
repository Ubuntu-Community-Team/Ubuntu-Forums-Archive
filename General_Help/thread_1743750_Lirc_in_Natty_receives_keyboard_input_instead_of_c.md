---
title: "Lirc in Natty receives keyboard input instead of correct IR-signal from remote"
date: 2011-04-29
forum: General Help
---

### Post by gunnarflax on 2011-04-29
Hi! I have just recently made a custom configuration of Ubuntu Server 11.04 for use as a HTPC with XBMC 10.1. The problem is that when I install lirc in 11.04 (never had this problem in 10.04) and run **irw** it receives keyboard input instead of the correct IR-code. I read something about this problem [here]("http://ubuntuforums.org/showpost.php?p=9984844&postcount=4") but didn't understand it completely. Can anyone help me to make it behave as it should? My remote is a (Soundgraph) Antec Veris rm200.

---

### Post by mooscape on 2011-04-30
Similar problem here. XBMC on Ubuntu 11.04 on an Asrock 100HT but the Infra-red buttons are not all working. (eg "OK" and "play" are dead, while "left" and "right" are working. The only way I could get them to work last time on 10.10 was by following the instructions on the Asrock site. This caused all kinds of other problems when I tried to use synaptic. Surely there must be away around all of this?

---

### Post by gunnarflax on 2011-04-30
Ok, good that I'm not the only one, I will check out the xbmc forum and see if anyone has found a solution.

---

### Post by hyponoia on 2011-05-06
Hello. Any further input on this one? I've got the same thing,  Ubuntu 11.04 on an Asrock 100HT, direction buttons, volume up, down and mute as well as clear and enter work as keyboard inputs, nothing else out of the box. Was working wonderfully on 10.10 with Asrock provided drivers - what a shame that the upgrade fixed so many other problems for me or I'd just go back!

Have got LIRC working with the kernel driver (nuvoton-cir) and can get everything going by changing the protocol to RC-6 (sudo ir-keytable -p RC-6 ) but still get the keyboard inputs. If I press one of the above buttons, I get multiple keyboard inputs and an LIRC code so a listening application gets input from too many places. 

I think I would be fine if I could just disable the keyboard handler from the input device, but no amount of google seems to lead me to how to do that - is it defined in the driver?

cat /proc/bus/input/devices
...
I: Bus=0019 Vendor=1050 Product=00b4 Version=0073
N: Name="Nuvoton w836x7hg Infrared Remote Transceiver"
P: Phys=
S: Sysfs=/devices/virtual/rc/rc0/input4
U: Uniq=
H: Handlers=kbd event4
B: PROP=0
B: EV=100013
B: KEY=fff 0 200108fc326 237605100000000 0 700158000 419200100001
9e968000000000 10000000
B: MSC=10

Does anyone know how I could go about removing the kbd handler from this device? I assume that the generic event4 handler is the one to pass the ir scancodes to LIRC and kbd sends the keyboard inputs...

---

### Post by gunnarflax on 2011-05-06
I'm completely stuck on this problem and I can't use 10.10 since 11.04 fixed every other problem I was having with this HTPC build. The only thing not working for me is the remote.

I've been trying to find a solution to this on the xbmc forum and maybe this thread will help you:

[http://forum.xbmc.org/showthread.php?p=787084](http://forum.xbmc.org/showthread.php?p=787084)

If you have any ideas I could try, please let me know :)

---

### Post by hyponoia on 2011-05-06
Thanks for the link mate. That's ground I've already covered, but it's appreciated all the same.

I think I'm just going to have to use the keyboard for a while as I've been trying to sort this out for days (literally, days!).

Happy to help you trouble shoot though - I think I've got some knowledge even though I can't sort out my own problems.

What do you get out of ir-keytable? What's your /etc/lirc/hardware.conf look like? Have you tried using inputlirc? Or Eventlirc (couldn't get it to compile myself, but it looked promising for a while)?

---

### Post by gunnarflax on 2011-05-10
I haven't tried any lirc alternatives since I don't believe that will fix anything, I will still have the conflicting default modules. From **ir-keytable** I get:

```
Found /sys/class/rc/rc0 (/dev/input/event5)
   Driver imon, table rc-imon-pad
   Supported protocols: RC-6
   Enabled protocols:
   Repeat delay = 500 ms, repeat period = 33 ms
```

My /etc/lirc/hardware.conf looks like this:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON Antec Veris"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-antec-veris"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```

Can this help in any way? From what I understand when reading the ir-keytable input then it's the driver imon that get's automatically loaded and conflicts with lirc?

---

### Post by gunnarflax on 2011-05-10
Hah! I think I found the solution. Read [this page]("http://wilsonet.com/?page_id=95") and escpecially paragraph seven and see what you make out of it! Also read [this]("http://wilsonet.com/?page_id=99").

---

### Post by gunnarflax on 2011-05-10
I didn't exactly understand what was supposed to be done so please help me with it if you understand it better than I did. The second link in the previous post described more on how you should fix the issue.

---

### Post by darkscout on 2011-05-10
[ir-keytable or: How I Learned to Stop Worrying about the LIRC Kernel]("http://ubuntuforums.org/showthread.php?t=1754719")

---

### Post by hyponoia on 2011-05-10
Just at work now, but I'll have a closer look at these tonight. I'd read most of the things on Jarod's blog but the imon stuff is new on me.

darkscout's stuff looks very, very promising, so I'll give that a go first and see what comes of it. 

gunnarflax - I do notice that /dev/input/event5 says it only supports RC-6 and has nothing enabled. What happens if you try ```
ir-keytable -p LIRC
```or (I think equivalently) 
```
echo lirc > /sys/class/rc/rc0/protocols
``` ?

---

### Post by hyponoia on 2011-05-11
Ok, so darkscout's link is a very nice post about how to go about using ir-keytable and the devinput driver for LIRC but it doesn't fix the problem of receiving keyboard inputs in addition to the scan codes (at least in my case).

gunnar, what darkscout writes about is pretty much precisely what your links are on about, so try to follow his guide as it's the best I've seen so far when it comes to using the devinput driver for LIRC.

For anyone else following along, I've found useful information about HAL conflicts here that seem to describe my problem exactly: 
[http://lirc.org/html/devinput.html ]("http://lirc.org/html/devinput.html")

However, trying to get HAL to ignore the input from my device doesn't seem to work. I've created a file at ```
/usr/share/hal/fdi/preprobe/20thirdparty/10-ignore-nuvoton.fdi
```which contains
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
 <match key="info.product" contains_ncase="Nuvoton w836x7hg">
    <merge key="info.ignore" type="bool">true</merge>
 </match>
</device>
</deviceinfo>
```and on reboot lshal produces
```
udi = '/org/freedesktop/Hal/devices/temp/174'
  info.ignore = true  (bool)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Ignored Device'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ignored-device'  (string)
  input.device = '/dev/input/event4'  (string)
  input.product = 'Nuvoton w836x7hg Infrared Remote Transceiver'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/rc/rc0/input4/event4'  (string)
```Which is all well and good, but HAL STILL picks up input off the supposedly ignored device.

Anyone have any ideas of where I might be going wrong?

---

### Post by hyponoia on 2011-05-11
Sweet chocolate Jesus, I think I've figured out how to get the keyboard inputs to stop: by getting X to ignore them.

[http://naiveprogrammer.blogspot.com/2011/01/linux-xorg-configuration.html](http://naiveprogrammer.blogspot.com/2011/01/linux-xorg-configuration.html)

Following the above, I've added my remote to the xorg.conf file
```
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
```by adding these lines:
```
Section "InputClass"
        Identifier "Nuvoton Remote USERDEFINED"
        Driver      "evdev"
        MatchProduct "Nuvoton w836x7hg Infrared Remote Transceiver"
        Option "Ignore" "on"
EndSection
```After a reboot, we see this in ```
cat /var/log/Xorg.0.log | grep Nuvoton
``````
[    25.240] (II) config/udev: Adding input device Nuvoton w836x7hg Infrared Remote Transceiver (/dev/input/event4)
[    25.240] (**) Nuvoton w836x7hg Infrared Remote Transceiver: Ignoring device from InputClass "Nuvoton Remote USERDEFINED"
```which tells us that the remote is finally being ignored as a keyboard by X!!!

Now my LIRC is working happily with inputlirc only receiving the scancodes and passing them on to the socket... now to go grapple with the keymaps, because I haven't already wasted enough time getting a bloody remote to work!

---

### Post by gunnarflax on 2011-05-11
> **hyponoia said:**
> 
gunnarflax - I do notice that /dev/input/event5 says it only supports RC-6 and has nothing enabled. What happens if you try ```
ir-keytable -p LIRC
```or (I think equivalently) 
```
echo lirc > /sys/class/rc/rc0/protocols
``` ?

When I do that it acts as it always do. ir-keytable -t gives the correct output for every pressed button, when I run irw I get just the keyboard output.

> **hyponoia said:**
> Sweet chocolate Jesus, I think I've figured out how to get the keyboard inputs to stop: by getting X to ignore them.

[http://naiveprogrammer.blogspot.com/2011/01/linux-xorg-configuration.html](http://naiveprogrammer.blogspot.com/2011/01/linux-xorg-configuration.html)

Following the above, I've added my remote to the xorg.conf file
```
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
```by adding these lines:
```
Section "InputClass"
        Identifier "Nuvoton Remote USERDEFINED"
        Driver      "evdev"
        MatchProduct "Nuvoton w836x7hg Infrared Remote Transceiver"
        Option "Ignore" "on"
EndSection
```

I'm not a very advanced linux user and didn't get everything he said in the page you linked to but I would like to try out your solution to get it to stop receiving keyboard input. The thing I wonder is how you  retrieved the information for Identifier, MatchProduct and Driver?

If I can get help on using the devinput driver as well it'd be much appreciated!

---

### Post by hyponoia on 2011-05-11
> The thing I wonder is how you  retrieved the information for Identifier, MatchProduct and Driver?The best place to find this would be from udevadm or the X log.
```
udevadm info --export-db > ~/Documents/udev.txt
or
cat /var/log/Xorg.0.log
```Here I redirect the output of udevadm to a text file in ~/Documents for easier access. Then you can open that file with gkedit or kate or whatever you like.

From udev, you'll have to search for something like this (mine):
```
P: /devices/virtual/rc/rc0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/rc/rc0
E: NAME=rc-rc6-mce
E: DRV_NAME=nuvoton-cir
E: SUBSYSTEM=rc

P: /devices/virtual/rc/rc0/input4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/rc/rc0/input4
E: PRODUCT=19/1050/b4/73
E: NAME="Nuvoton w836x7hg Infrared Remote Transceiver"
E: PROP=0
E: EV=100013
E: KEY=fff 0 200108fc326 237605100000000 0 700158000 419200100001 9e968000000000 10000000
E: MSC=10
E: MODALIAS=input:b0019v1050p00B4e0073-e0,1,4,14,k71,72,73,74,77,80,94,A1,A4,A7,A8,AE,CF,D0,D2,D4,E0,E1,E2,160,164,166,16D,16E,170,171,172,174,175,179,181,182,185,188,189,18E,18F,190,191,192,193,197,19C,1A9,200,201,202,203,204,205,206,207,208,209,20A,20B,ram4,lsfw
E: SUBSYSTEM=input

P: /devices/virtual/rc/rc0/input4/event4
N: input/event4
S: input/irremote
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/rc/rc0/input4/event4
E: MAJOR=13
E: MINOR=68
E: DEVNAME=/dev/input/event4
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_KEY=1
E: XKBMODEL=pc105
E: XKBLAYOUT=us
E: DEVLINKS=/dev/input/irremote
E: XKBOPTIONS=lv3:ralt_switch
E: DMI_VENDOR=To Be Filled By O.E.M.
```It will probably take some looking, but will likely be close to lines about "/rc0" or if you already know which /dev/input/eventX your ir receiver is getting mapped to (in my case, /dev/input/event4), look around there. You want the E:NAME= Field to put in MatchProduct for the xorg rule. 

The driver evdev is probably what is already being used by your ir receiver as the keyboard driver, so try that. If you want to be sure you'll have to check  /var/log/Xorg.0.log which should give you details of which rule is used to configure it as an input device and you can work backwards from there.

Once you've found something to enter for MatchProduct, stick it in as previously posted and you should be able to get X to ignore inputs from that device.

Just have to head to work now, but I'll try to write something about how I've used inputlirc and the devinput driver to get LIRC to recognize my device when I get some time today (GMT+10, just starting the day).

---

### Post by hyponoia on 2011-05-11
So I've just realized that to get a working LIRC socket, I had to use inputlirc and that LIRC is only providing libraries and irw for testing. Here I was thinking LIRC was doing the heavy lifting, but it was mostly just getting in the way.

The way I'm going about it might be the most bass-ackwards way in existence, and I'd love it if someone with more knowledge than me could give a better way, but what the hell, it works.

In short, I think the steps look like this:
[LIST=1]
[*]Install ir-keytable package.

[*]Test that ir keys make it through a driver using a supported protocol ```
ir-keytable -t

```

[*]Disable X from receiving keyboard inputs off the device if that applies to you (say if you get ^[[D in front of a 'left' ir button press registered while testing using ir-keytable or if you can get a previous command by pressing 'up' in a terminal prompt, this is happening to you). <See previous posts>

[*]Install LIRC and inputlirc packages. 

[*]Configure LIRC however, I don't think it matters as we'll use inputlirc to run things, LIRC is just there for libraries and to provide irw for testing (I think).

[*]Make sure you are still getting ir key presses using ir-keytable -t. LIRC likes to change the rc protocols to LIRC and break things for me. In my case, I have to run ir-keytable -p RC-6 to change it back.

[*]Determine /dev/input/eventX that your ir remote is being mapped to if you haven't already. I think just running ir-keytable will tell you this.

[*]*Optional but recommended* Use udev rules to make your ir device static. See here: [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php) under the heading "Make the LIRC Device Static"

[*]Start inputlirc by pointing it at the /dev/input/eventX or static mapping (I used irremote as in the example linked):
```
inputlircd /dev/input/eventX

or

inputlircd /dev/input/irremote
```

[*]Test that the socket is issuing LIRC commands:
```
irw /dev/lircd
*yes, it should be /dev/lircd and not /dev/lirc0 as we're using inputlirc
```

[*]Once you have everything working, you'll want to write the appropriate commands in to /etc/rc.local so they are run every time your system boots. My rc.local contains this:
```
ir-keytable -p RC-6 #corrects ir-receiver protocol
inputlircd /dev/input/irremote #starts inputlirc and tells it which device to use
```

[*]After that you get the fun job of configuring all the keytables, which I'm in the middle of doing so I don't know much about that yet.
[/LIST]

This is probably a ridiculous way of getting things to work and I've probably missed some vital bit that would make things much easier. Truly hope that the next post is some ir genius saying, "Well, that's crazy, why wouldn't you just to the much easier XXX" so anyone else who thought they did their research by buying a product that was supposedly supported in *nix doesn't go through the same insanity.

---

### Post by hyponoia on 2011-05-16
I have now got this working without inputlirc by using the /dev/input driver method outlined by darkscout. It is still required in my setup to get X to ignore keyboard inputs off my remote.

The only other quirk I have is that LIRC needs to be restarted a few times before it seems to work, so my ugly workaround is have the following lines in my /etc/rc.local to run at boot.

```
service lirc restart
service lirc restart
service lirc restart
ir-keytable -p RC-6 -p LIRC
```

Hope it helps someone!

---

### Post by oct on 2011-07-26
Hello everyone, and hello hyponoia!

Very useful post. I followed your instructions on how to setup my remote with ir-keytable and inputilrcd and have found some problems.

First, adding this lines at the end of 11-evdev-quirks.conf 

Section "InputClass"
        Identifier "Imon remote"
        Driver      "evdev"
        MatchProduct "iMON Panel, Knob and Mouse(15c2:ffdc)"
        Option "Ignore" "on"
EndSection

does nothing. cat /var/log/xorg.0.log | grep Imon shows this:

[    13.841] (**) iMON Panel, Knob and Mouse(15c2:ffdc): Ignoring device from InputClass "Imon remote"

but keypresses are not being ignored.

Second, if I try to run "inputlircd /dev/input/remote" it tells me that I don't have permissions. I have to do it as sudo. Do you know if I can run it as sudo in the rc.local file?

Third, if I start all manually, inside Mythtv all the keypresses are repeated. The keys that work out of the box are repeated 3 times. For example, the arrow keys. I think one corresponds on the keypresses not being ignored, but I don't know why the other two repeats. The keys that do not work out of the box (play, pause, etc.) are repeated twice. Do you know something about this?

Thanks

Oct

---

### Post by hyponoia on 2011-07-26
> 
Section "InputClass"
Identifier "Imon remote"
Driver "evdev"
MatchProduct "iMON Panel, Knob and Mouse(15c2:ffdc)"
Option "Ignore" "on"
EndSection

does nothing. cat /var/log/xorg.0.log | grep Imon shows this:

[ 13.841] (**) iMON Panel, Knob and Mouse(15c2:ffdc): Ignoring device from InputClass "Imon remote"

but keypresses are not being ignored.


Humm, all I can think of is that either the E:NAME you've picked out isn't right or that evdev isn't the driver that X is supposed to ignore for your remote. I think there should be some hints in /var/log/Xorg.0.log as to the driver name if you want to go hunting, but honestly I wouldn't know exactly what you're looking for. Is that the only line mentioning iMON? Because I think that would be suspect if it was.

> Second, if I try to run "inputlircd /dev/input/remote" it tells me that I don't have permissions. I have to do it as sudo. Do you know if I can run it as sudo in the rc.local file?

Everything run in rc.local has root privileges, so if it's only a permissions issue, you're set. I would wonder why though - are you sure LIRC isn't also running along side inputlirc? That could possibly help explain (I'm way out on a limb here, because I don't think it would work even if that was the case but...):

> Third, if I start all manually, inside Mythtv all the keypresses are repeated. The keys that work out of the box are repeated 3 times. For example, the arrow keys. I think one corresponds on the keypresses not being ignored, but I don't know why the other two repeats. The keys that do not work out of the box (play, pause, etc.) are repeated twice. Do you know something about this?

Does this only happen in MythTV or do you see it with irw or ir-keytable -t as well? Before I had X ignoring keypresses, I'd get an indeterminate amount for some buttons depending on how long the button was held down. Could be anything up to 4 for even a momentary press. I'd work on #1 of getting X to ignore first and see if that doesn't sort it.

---

### Post by oct on 2011-08-05
Thanks for your quick reply. After a little investigation I found that my remote was listed as two different devices in Xorg.0.log. So, I had to add two sections in the 11-evdev-quirks.conf:
[INDENT]
Section "InputClass"
        Identifier "iMON remote"
        Driver      "evdev"
        MatchProduct "iMON Panel, Knob and Mouse(15c2:ffdc)"
        Option "Ignore" "on"
EndSection

Section "InputClass"
        Identifier "iMON remote 2"
        Driver      "evdev"
        MatchProduct "iMON Remote (15c2:ffdc)"
        Option "Ignore" "on"
EndSection[/INDENT]

After that a cat /var/log/Xorg.0.log | grep iMON shows:

[INDENT][    20.550] (II) config/udev: Adding input device iMON Panel, Knob and Mouse(15c2:ffdc) (/dev/input/event2)
[    20.550] (**) iMON Panel, Knob and Mouse(15c2:ffdc): Ignoring device from InputClass "iMON remote"
[    20.551] (II) config/udev: Adding input device iMON Panel, Knob and Mouse(15c2:ffdc) (/dev/input/mouse0)
[    20.551] (**) iMON Panel, Knob and Mouse(15c2:ffdc): Ignoring device from InputClass "iMON remote"
[    20.551] (II) config/udev: Adding input device iMON Remote (15c2:ffdc) (/dev/input/event3)
[    20.551] (**) iMON Remote (15c2:ffdc): Ignoring device from InputClass "iMON remote 2"[/INDENT]

and the remote is efectively ignored by X! (oct 1 - remote control 0) :)

Now, inside Mythtv, I receive two keypresses every time, instead of the three that I had before. (oct 1 - remote control 1) :(. In irw, I get only one keypress per key, unless I hold the button enough time. In ir-keytable, I see always two events, one for the key down (press), and another for the key up (release). Could this be the cause of the repeated keypresses? 

Also, inside Mythtv, there is a remote control section that I have to configure to point to /dev/lircd. If I change or delete this setting, remote simply does nothing. Could be that Mythtv listens directly to the lirc socket and causes the repeated events?

I'm lost here...

Oct

---

### Post by oct on 2011-08-11
I won! The only problem I had with the duplicate keypresses was caused by a wrong /home/username/-lirc/mythtv file. This file was generated automatically with Mythbuntu control centre and, don't ask me why, it had duplicate entries for every key. I had to create a new one and enter manually every key in the remote. Now it works!

Thanks

Oct

---

