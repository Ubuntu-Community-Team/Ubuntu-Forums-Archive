---
title: "Remove mouse feature in /proc/bus/input/devices"
date: 2011-01-07
forum: General Help
---

### Post by 8301 on 2011-01-07
Hello 

ubuntu 10.10

I have a remote control (imon --> Harmony) that acts like a mouse. My goal is to remove that feature. Iam using lirc with Linux input layer (/dev/input/eventX) because Imon driver doesn't work at all. To get Linux input layer to work you need to choose the imon device.

```
cat /proc/bus/input/devices
```

```
I: Bus=0003 Vendor=15c2 Product=ffdc Version=0000
N: Name="iMON Remote (15c2:ffdc)"
P: Phys=usb-0000:00:12.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/rc/rc0/input2
U: Uniq=
H: Handlers=kbd mouse0 event2 
B: EV=100007
B: KEY=fff 0 400000108c0320 2d5008200000000 30000 400119000 419614100801 809e168000000000 200000010004002
B: REL=103

```

The only problem with this setup is that my direction buttons on the remote pics up like a mouse not key presses like up, down, right, left. So when I turn on irw in the terminal it still acts like a mouse and irw doesn't react at all. 

I think it is because of this line

```
H: Handlers=kbd mouse0 event2 
``` 

How can I remove mouse0 from handlers or change lirc so it pics up the mouse signal and convert it to key presses.
Thanks

---

### Post by 8301 on 2011-01-07
bump

---

### Post by 8301 on 2011-01-07
bumping

---

### Post by 8301 on 2011-01-08
triple bump

---

### Post by 8301 on 2011-01-09
quadbump

---

### Post by wiltk on 2011-01-15
> **8301 said:**
> The only problem with this setup is that my direction buttons on the remote pics up like a mouse not key presses like up, down, right, left. So when I turn on irw in the terminal it still acts like a mouse and irw doesn't react at all. 

I doubt if if this will help, but I have seen (and may be wrong, I don't have this remote) in other threads that the remote has a button to switch the functions of the directions from mouse to directional.  On startup, the arrows act as a mouse and you have to press the button to switch to directionals.

Further, it looks like this thread: [http://ubuntuforums.org/showthread.php?t=1161574&page=7]("http://ubuntuforums.org/showthread.php?t=1161574&page=7") has some ideas on how to get an imon working.

Good luck and I hope you have better luck getting your remote working than I am.

---

### Post by MacLeod_1980 on 2011-02-24
I would love to know how you got this device (Vendor=15c2 Product=ffdc) working in ubuntu 10.10 - for the life of me I cannot get irw to recognize it at all.

If I can get it working, I will most likely be in the same predicament as you - then maybe I can help with some testing.

Would you be able to share the details of how you got the device working?

What I have done so far (not working):

```
cat /proc/bus/input/devices
```

Resulted in the following:

```
I: Bus=0003 Vendor=15c2 Product=ffdc Version=0000
N: Name="iMON Remote (15c2:ffdc)"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/rc/rc0/input6
U: Uniq=
H: Handlers=kbd mouse1 event6 
B: EV=100007
B: KEY=fff 0 0 400000 108c0320 2d50082 0 0 30000 4 119000 4196 14100801 809e1680 0 2000000 10004002
B: REL=103

```

I then installed lirc and configured it  to an eventX device and chose event6.

The knob on my Antec box works, but the IR picks up nothing from my harmony, or any mce remote I point at it.

What does your hardware.conf and lircd.conf files look like?  They are in:

```
cd /etc/lirc/
```

I also wonder if you have any imon specific components blacklisted in the following location:

```
cd /etc/modprobe.d/
```

Specifically in files like blacklist.conf, in the location above - however several tutorials I have tried to get this working talk of blacklist-imon.conf or blacklist-lirc_imon.conf - so it may be some variant. (such ast he following one [http://forum.xbmc.org/showthread.php?t=83284](http://forum.xbmc.org/showthread.php?t=83284))

And finally, do you have an options file associated with your device?

```
/etc/modprobe/lirc_imon.conf
```

It may not be called this file exactly... may be something like lirc.conf.

In fact, thinking about it, this is probably what you need for your situation, an options file with nomouse specified in it!

Like this:
```
options lirc_imon debug=1 nomouse=1
```

In:```

/etc/modprobe.d/lirc.conf
```

---

### Post by MacLeod_1980 on 2011-03-02
*bump* Anyone?

---

### Post by chrismurf2900 on 2011-03-06
Take a look at an old post I had which fixed my issues with the imon driver (device ID 15c2):
[http://ubuntuforums.org/showthread.php?t=1609652](http://ubuntuforums.org/showthread.php?t=1609652)

Also, and this may be the better more informative place to go, I have posted instructions on MythTV's wiki directing people with this issue on how to solve it.
Here's that link: [http://www.mythtv.org/wiki/Soundgraph_iMON_Antec_Veris_Mythbuntu_10.10](http://www.mythtv.org/wiki/Soundgraph_iMON_Antec_Veris_Mythbuntu_10.10)

I'm looking at having the "Toggle" button automatically "pressed" once my MythTV box has started up, so that I don't have to press Toggle every time to get out of the Mouse mode.  I'll try to remember to post my results here for that.

I hope all that helps.  Good luck!

---

### Post by MacLeod_1980 on 2011-03-07
The interesting thing for me is you are using ffdc version of 15c2.

I have tried the information you linked to with no success.  ANy chance you could provide me with your lirc.conf, hardware.conf and any blacklist and option files you may have - I think the blacklist and options files will be key to my success.

So really I need the help of the original poster.

---

### Post by 8301 on 2011-03-16
Hello

Iam sorry to say that I have not solved this problem yet :( 

I followed this guide to get my imon remote to work

[XBMC forum]("http://forum.xbmc.org/showthread.php?t=83284")

But Iam still struggling with the mouse problem but the search have been on ice the past month. I would love to hear if you succeed or not

---

### Post by MacLeod_1980 on 2011-04-14
Did you read my post where I mentioned trying the following for your mouse issue?

options lirc_imon debug=1 nomouse=1

Worth a shot I figure.  I have yet to try the link you sent, but believe I have in the past - my problem is I get nothing from IRW, evern when removing old drivers, and configuring to be event.

I just read this - posted yesterday in the link you provided:

Quote:
Originally Posted by Krautmaster View Post
Does anybody know how to set the KeyMode to default. My Remote is always MouseMode so i have to press the key above the joystick once...
Compile the imon module from git. That fixes this problem (and the repeating/stuck key presses).

---

