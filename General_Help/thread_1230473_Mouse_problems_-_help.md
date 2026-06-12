---
title: "Mouse problems - help?"
date: 2009-08-03
forum: General Help
---

### Post by loctavius on 2009-08-03
Ok, here is a weird one. Tried IRC, but it was WAY to busy to get help in there.

My mouse keeps freezing. It happens sometimes 30 seconds after I log in, sometimes 15 minutes, but it ALWAYS happens. It seems like it is just losing connectivity to the mouse. I've tried several brands of USB mice. (This computer does not have the older type mouse or keyboard ports, it is all USB) It did not EVER happen under Windows. 

The computer is a generic Dell I bought about two years ago. It came with Windows XP, which is what it ran for a few months. Then I wiped the drive and put Ubuntu on it. I use it only as a Samba server for the home network and to run SETI@home software. I just installed 8.04 (I think that is the right version number) and got everything back up and running again. I had the same issue with the mouse when I was running a 6.x version of Ubuntu. The keyboard has always worked just fine.

Under the earlier version of Ubuntu, I could unplug the mouse, and plug it back in, and it worked. Since I've upgraded, that trick no longer works. Once the mouse dies, it is dead until I reboot.

Any thoughts? This is killing me here, I'm tired of rebooting it every five minutes. Thanks.

---

### Post by Volt9000 on 2009-08-03
Is it a wired or a wireless mouse? I'm assuming wired, but I'll ask just to be sure.

Try this: when your mouse dies, bring up a Terminal session by hitting Alt+F2 and typing in the box:

```

gnome-terminal

```

and pressing Enter. Then in the terminal type

```

dmesg | tail -20

```

This will give you a printout of any important system-related stuff that's been going on. If Linux disconnected your mouse, it should have a record of it here.

---

### Post by loctavius on 2009-08-03
> **Volt9000 said:**
> Is it a wired or a wireless mouse? I'm assuming wired, but I'll ask just to be sure.

Try this: when your mouse dies, bring up a Terminal session by hitting Alt+F2 and typing in the box:

```

gnome-terminal

```and pressing Enter. Then in the terminal type

```

dmesg | tail -20

```This will give you a printout of any important system-related stuff that's been going on. If Linux disconnected your mouse, it should have a record of it here.

Yes, it is wired. All the mice I've tried have been wired. I figure if I can't get them to work, I'm sure not going to get a wireless running reliably. Ok, it just happened again. Here is what I got when I ran the dmesg command as you showed me. By the way, the light under the scroll wheel stays lit when it freezes up, I don't know if that means anything or not. I transcribed what showed up in the terminal window exactly as it showed up.

[81.120885] Marking TSC unstable due to: cpufreq changes.
[81.135481] Time: acpi_pm clocsource has been installed.
[81.319927] Clocksource tsc unstable (delta = -99679383 ns)
[83.104912] Bluetooth: Core ver 2.11
[83.105816] NET: Registered protocol family 31
[83.105824] Bluetooth: HCI device and connection manager initialized
[83.105832] Bluetooth: HCI socket layer initialized
[83.175459] Bluetooth: L2CAP ver 2.9
[83.175469] Bluetooth: L2CAP socket layer initialized
[83.233990] Bluetooth: RFCOMM socket layer initialized
[83.234021] Bluetooth: RFCOMM TTY layer initialized
[83.234024] Bluetooth: RFCOMM ver 1.8
[85.929593] 0000:04:09.0 tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[85.929610] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[86.339575] NET: Registered protocol family 17
[92.218589] NET: Registered protocol family 10
[92.219386] lo: Disabled Privacy Extensions
[92.221443] ADDRCONF (NETDEV_UP): eth1: link is not ready
[104..352199] eth0: no IPv6 routers present

---

### Post by loctavius on 2009-08-03
bump

---

### Post by finch127 on 2009-08-03
how about this:

type lsusb in a terminal and hit enter

it might tell you that it needs a package, i dont know what package but just install what it asks you to install, and then do this:

type lsusb and hit enter.

the output should be like this:
```

finch@Kratos:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 1130:f211 Tenx Technology, Inc. USB audio headset
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Now in my case, by looking at that output, I can see that the only thing plugged in that is USB that is not my USB Audio headest is my mouse, the one that says Holtek Semiconductor. You should try this and find something similar, whatever the manufacturer name of the mouse is. Then knowing this information right here:

Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 

We can get more info.

Do this then, look at the line above in my example and you will see Bus = 002 and device = 002 so then:

```

lsusb -v -s whateveryourbus#was:whateveryourdevice#was

so mine would be

lsusb -v -s 002:002

```

Please post the output of that command and we might find something

---

### Post by finch127 on 2009-08-03
oh man i am in idiot, where it says:

```

lsusb -v -s 002:002

it should have sudo in front to get the device status

so then

sudo lsusb -v -s 002:002

```

sorry! Try this command when your mouse is frozen and you have a terminal up

---

### Post by loctavius on 2009-08-03
> **finch127 said:**
> how about this:

type lsusb in a terminal and hit enter

it might tell you that it needs a package, i dont know what package but just install what it asks you to install, and then do this:

type lsusb and hit enter.
Ok, We have a problem. No lsub.

lsub [enter]
bash: lsub: command not found

so I tried
sudo lsub [enter] [password entered]
sudo: lsub: command not found

Using Heron (8.04 LTS) 

Now what? (Just to be sure I'm not a complete moron, I tried (one)sub and |sub too, to make sure I wasn't misreading your post. Nothing worked.)

I appreciate the assistance by the way. Although I haven't actively used a *nix box in several years, I started on *nix systems both as a hobby and professionally (networking them for VOIP applications) for over ten years. I've forgotten so much I'll probably never recover, and this is a stupid freaking problem to have. So I sincerely do appreciate the help. I'm not a n00b - just brain dead after years of in-activity. :P

---

### Post by Volt9000 on 2009-08-03
It's lsusb, not lsub. As in "list USB".

---

### Post by loctavius on 2009-08-03
> **Volt9000 said:**
> It's lsusb, not lsub. As in "list USB".

*facepalm*

Follow simple instructions FAIL - working on it now. thx.

---

### Post by finch127 on 2009-08-03
Yeah hey lol happens to all of us man. Keep me updated :D

---

### Post by loctavius on 2009-08-03
Retyping all of this on a second computer after the mouse freezes sucks. Ugh. I have of course forgotten how to pipe the output to a file I could post. Even if I knew, I'm not familiar enough with Linux keyboard shortcuts anymore to manage it. Oh well.

Ok, output of lsusb was this:

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1241:1166 Belkin optical mouse w/ scrollwheel (PS: It is a Dynex mouse, not Belkin)
Bus 001 Device 002: ID 413c:2003 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000

It did not ask me to install any packages.

Next I did the sudo lsusb -v -s 001:003 and got all of this:

Bus 001 Device 003: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Device Descriptor:
  blength                                18
  bDescriptorType                    1
  bcdUSB                                1.10
  bDeviceClass                        0 (Defined at the interface level)
  bDeviceSubClass                  0
  BDeviceProtocol                    0
  BMaxPacketSize0                  8
  idVendor                              0x1241 Belkin
  idProduct                              0x1166 optical mouse w/ scrollwheel
  bcdDevice                            2.70
  iManufacturer                        0
  iProduct                                0
  iSerial                                   0
  bNumConfigurations               1
  ConfigurationDescripto:
     bLength                              9
     bDescriptorType                 2
     wTotalLength                      34
     bNumInterfaces                  1
     bConfigurationValue            1
     iConfiguration                     0
     bmAttributes                       0xa0
        (Bus Powered)
        Remote Wakeup
     MaxPower                          100mA
     Interface Descriptor:
         bLength                          9
         bDescriptorType             4
         bInterfaceNumber           0
         bAlternateSetting            0
         bNumEndpoints               1
         bInterfaceClass              3 Human Interface Device
         bInterfaceSubClass        1 Boot Interface Subclass
         bInterfaceProtocol           2 Mouse
         iInterface                       0
            HID Device Descriptor:
               bLength                       9
               bDescriptorType          33
               bcdHID                      1.10
               bCountryCode            0 Not Supported
               bNumDescriptors         1
               bDescriptorType          34 Report
               wDescriptorLength        52
              Report Descriptors:
                     ** UNAVAILABLE **
        Endpoint Descriptor:
           bLength                         7
           bDescriptor Type            5
           bEndpointAddress           0x81   EP   1   IN
           bmAttributes                      3
              Transfer Type                           Interuppt
              Synch Type                              None
              Usage Type                               Data
            wMaxPacketSize              0x0008  1 x 8 bytes
            bInterval                       10
Device Status:            0x0000
       (Bus Powered)

++++++++++END OF OUTPUT+++++++++++

Whew. The formatting is a bit wacky since I was transcribing it visually from one monitor into this post, but you get the idea. Thanks again.

---

### Post by finch127 on 2009-08-03
WOW man you typed that? Well hey, just so you know for future reference, if you want to pipe the output to another command:

```

lsusb blah blah blah | next command

```

And if you want to send it direct to a textfile

```

lsusb blah blah > name.txt

```

So then... its bad news D:

It seems that the mouse is fine and so is the bus its plugged in to. At least, as far as I can see from the bus info. Oh and dont worry about the fact that it says its a belkin mouse, it probably uses Belkin's chips and technology inside and has been rebranded. Mine is a pro-micro mouse and it says Holtek Semiconductors so I assume thats the manufacturer? idk but its not important.

Anyway, I do believe the problem is in your X-Server. Try this:

Boot in, and make a copy of your /etc/X11/xorg.conf file and rename it [YOU MUST DO THIS!]. if your mouse does not work you can do this through the command line like this:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Next time you boot, use the option that says recovery mode and it will take you to a blue screen. For good measure, run fsck [not necessary but this is a since you're here type of thing] and then when thats done run the option that says fix X or configure X server or whatever. See if that fixes your mouse problem. WARNING**** This may break your desktop effects and you may not be able to use your graphical desktop so then do this, its why we make the backup:

Then continue normal boot, and if it black screens on you and you cant even get into your GDM, just wait a few minutes to be sure it's booted properly and type ctrl+alt+F2 to bring yourself to a system terminal. This is where the backup is handy, do:

```

sudo rm -rf /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```

Here we are basically deleting the configuration file produced by the system and replacing it with the backup if you want to do it graphically.

Then reboot and it should be back to the way it was before assuming it didnt work. If this does work, then you may have to live without fancy graphical effects but you will have mouse control and we can refer you to that thread.

Also, have you tried using the mouse on different USB ports? I cant really tell from the output of lsusb because i didnt ask about other buses, but just try it? Maybe it may work?

now also, is your computer a dell? you may want to try this:

[http://vanitdiscovery.blogspot.com/2009/05/ubuntu-904-keyboard-and-mouse-problem.html](http://vanitdiscovery.blogspot.com/2009/05/ubuntu-904-keyboard-and-mouse-problem.html)

Good Luck!

---

### Post by loctavius on 2009-08-03
> **finch127 said:**
> WOW man you typed that? Well hey, just so you know for future reference, if you want to pipe the output to another command:
 
((((SNIP))))

Good Luck!

First, thanks for all the help.

Second, it is getting late, so I'm going to give this a try tomorrow morning. If you would be so kind, would you look in on this thread when you get a chance? I'll post my progress then.

Third, even tho I have a nice, pretty desktop running, I'm not sweating it. The box is used as a Samba server for the home network, and it is currently running BONIC as well. (SETI and Rosetta) That is pretty much all I use it for. I may one day turn it into a Shoutcast server or something, but the point is, I can live without the bling if need be.

Last - THANKS again. A lot is coming back to me as I follow your directions, a lot more than I thought would. To think, I used to setup, configure, network, and run HP-UX L Class and N Class machines for a living. I was also a very proficient CCNA. And here I am, barely able to do the basics. Just goes to prove the old adage about losing it if you don't use it, but it is coming back. :) So regardless, the troubleshooting of this stupid problem that I have is fun for me, if frustrating. It's been a LONG time since I was a professional geek. :)

BTW - I teach middle school science now, no calling for hardcore *nix or networking skillz anymore.

---

### Post by finch127 on 2009-08-03
[CENTER]Also another possible idea, use the LiveCD if you have one and see if it works normally. If it does it could perhaps be a bad install but I doubt it. Also you can try booting into the safe GNOME session when you are at your GDM [login window]. Just click on session options and select safe GNOME. Try that too to see if it works straight. 

The fact that the mouse is still powered (the light is on) throughout all of this suggests that the mouse and bus are fine but its the OS that is having a problem. If all else fails I suggest backing up critical data, burning a new LiveCD and trying an install again, but I only would try this as a very very last resort. Perhaps switching to 9.04 would fix this? I still dont know but dont do this just yet! I have found though, that my other laptops many graphical issues were fixed all by a simple reinstall. Like I said though = LAST RESORT! When we dont know whats up and all else fails.[/CENTER]

---

### Post by finch127 on 2009-08-03
And thats fine man, I love doing this stuff! I find it challenging to see what is wrong. I will definitely check this up tomorrow.

---

### Post by loctavius on 2009-08-04
> **finch127 said:**
> And thats fine man, I love doing this stuff! I find it challenging to see what is wrong. I will definitely check this up tomorrow.
Found it. Will re-edit shortly.

---

### Post by loctavius on 2009-08-04
OK, here is everthing:

> **finch127 said:**
> 

Anyway, I do believe the problem is in your X-Server. Try this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup



Done.

> **finch127 said:**
> 
For good measure, run fsck


Could not see an option for fsck at the recovery screen.

> **finch127 said:**
> 
run the option that says fix X or configure X server or whatever


Done. It did break the desktop effects, but no biggie. Tested the mouse, froze after about 10 minutes.

> **finch127 said:**
> 
sudo rm -rf /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf


Done. Rebooted. Tested the mouse - broke after about 10 minutes.

> **finch127 said:**
> 
Also, have you tried using the mouse on different USB ports?


Done. Tried ports on the front and back of the computer. Mouse freezes after about 10 minutes no matter where I put it.

> **finch127 said:**
> 

now also, is your computer a dell? you may want to try this:

[http://vanitdiscovery.blogspot.com/2009/05/ubuntu-904-keyboard-and-mouse-problem.html](http://vanitdiscovery.blogspot.com/2009/05/ubuntu-904-keyboard-and-mouse-problem.html)


Computer is a Dell. It did not come with Ubuntu pre-installed, I did that. But I did everything mentioned in this thread, including editing of my /boot/grub/menu.lst file as mentioned, and the mouse still froze after about 10 minutes of use.

Just in case it got lost in the flurry of posts, I want to repeat that this has happened with two or three different mice, and it has also happened with THREE installs of Ubuntu. It happened on the 6.x version I had running a week or two ago before I upgraded, but at that time I could unplug the mouse, plug it back in, and it worked again. That doesn't happen with the Heron install I'm running now. 

So my point is if it has happened with three installs and two different kernels, I don't think it is an install problem.

Also, I don't have a LiveCD - I download the install images from the 'net and burn them myself.

I'm going to repeat something I said earlier just to vent - this is a stupid problem to have. Ugh. What now?

---

### Post by afrodeity on 2009-08-04
I could probably kick all the buntu-burks who check the old xorg.conf file first, expecting to see their mouse bouncing around in there, then wade off into the depths of lsusb and microchip bridges without actually getting to the point, which is if is a device, When in doubt, lsmod

check what happened to me recently
[http://ubuntuforums.org/showthread.php?t=1231333 ]("http://ubuntuforums.org/showthread.php?t=1231333")

---

### Post by finch127 on 2009-08-04
I think afrodeity's thread has this down so this is where i hand pass the buck -.-

Good Luck!

---

### Post by loctavius on 2009-08-04
> **afrodeity said:**
> I could probably kick all the buntu-burks who check the old xorg.conf file first, expecting to see their mouse bouncing around in there, then wade off into the depths of lsusb and microchip bridges without actually getting to the point, which is if is a device, When in doubt, lsmod

check what happened to me recently
[http://ubuntuforums.org/showthread.php?t=1231333 ]("http://ubuntuforums.org/showthread.php?t=1231333")
 

Ok, this moved a bit fast for me. I don't know if it was implied or not, but I had to sudo most of this to get a response back.

When I did the lsmod -v, it came back with:

usage: lsmod

So I just did lsmod and got a couple of screen worth of info. What exactly and I looking for? How does lsmod confirm the problem? And why is lsmod -v not working? (I'm using Heron, so I don't know if that matters) Keep in mind I'm just getting back into Linux after not really using it in about six years, so I need to have stuff explained a bit. I'm not a complete n00b, just rusty.

Then I did the modprobe stuff in your post and rebooted. (By the way, since I'm been kicking stuff around in my system at the direction of people, my system now hangs on restart, something it never did before. I have to pull the power plug to get it to restart)

Mouse still freezes. This time it didn't even last 10 minutes - it up and died after two. Can you help out Afrodiety?

For the record, if this was just going to continue being a Samba server with no other functions, I wouldn't care. But I'd REALLY like to start using this box as my primary system and get to loving Linux again. So it would be nice to have a mouse. :)

Thanks for any additional help.

---

### Post by finch127 on 2009-08-04
Hey if it hangs on restart you can try this:

hold alt+print screen, and type R E I S U B with a second delay between each press.

idk if that works when it hangs on restart, I have never had to use it for that, but hey, I am curious...

When your mouse freezes, try using ctrl+alt+F2 to go to a terminal. Log in, and come back using ctrl+alt+F7 and see if your mouse works again. All your open windows should be preserved. I dont know how exactly this works but I had a WM Hang on me earlier today and I tried that to mess around and suddenly it started working. Maybe it's coincidence maybe it can help?

Edit:
Could you kindly do this:

When your mouse freezes, use ctrl+alt+F2 again to go to a terminal and use dmesg again, only after it is frozen. Now, look at the output, and compare it to what is in afrodeity's post under the dmesg section. I just want to see if it is a similar problem because your last dmesg report shows nothing of the sort.

---

### Post by finch127 on 2009-08-04
An easy test to determine if it is X Windows, when your mouse freezes, try hitting ctrl+alt+backspace and it will take you to your GDM [login screen]. If your mouse works its X Windows, if it doesnt, it could be the module.

Also, some of this may help you:

[http://ubuntuforums.org/showthread.php?t=2663](http://ubuntuforums.org/showthread.php?t=2663)

Another thing I have found you may want to try, is this:

When your mouse freezes, go get another USB mouse that you have, and plug it into a different port to see if it works [keep the old mouse plugged in]

---

### Post by loctavius on 2009-08-04
> **finch127 said:**
> An easy test to determine if it is X Windows, when your mouse freezes, try hitting ctrl+alt+backspace and it will take you to your GDM [login screen]. If your mouse works its X Windows, if it doesnt, it could be the module.

Also, some of this may help you:

[http://ubuntuforums.org/showthread.php?t=2663](http://ubuntuforums.org/showthread.php?t=2663)

Another thing I have found you may want to try, is this:

When your mouse freezes, go get another USB mouse that you have, and plug it into a different port to see if it works [keep the old mouse plugged in]

Ok, I'll give all this a shot tomorrow then. Does this make day three or four of the Endless Broken Mouse Saga? :)

---

### Post by finch127 on 2009-08-04
Yes it does lol. Good Luck my friend, I will be back tomorrow to see how this is going. If afrodeity shows up, I am sure he has many more ideas as well.

---

### Post by afrodeity on 2009-08-05
Sorry. You have to use sudo modprobe -r XXXX the driver you wish to remove, and sudo modprobe XXXX where XXXX is the driver you want to unload/load. I try not to leave the sudo command lying around, because if you don't know how to use it, you shouldn't be playing with it, but  okay, you're not a n00b just rusty. :) Check the rest of my thread for stripping versioning information from the module, if this is preventing you from loading!

I see the link Loctavious gave you recommends unloading and loading the usbhid module.

First dmesg |tail to find out what went wrong. That should give you more of an idea of which module is the problem. 

It could also be a rare example of totally unsupported machine, in which case you could either compile the module youself from source, or upgrade to the next Linux kernel. Either way, you problem should be resolved, unless its a hardware issue. Try all the various module routines before you throw away the laptop.

---

### Post by afrodeity on 2009-08-05
Please post contents of dmesg | tail we can troubleshoot from there!

---

### Post by loctavius on 2009-08-05
> **afrodeity said:**
> Please post contents of dmesg | tail we can troubleshoot from there!

Ok, long post. I have posted below the contents of the dmesg output, (dmseg | -20), lsmod output, and lsusb output. I won't do anything else until I hear from one or both of you.

++++++++++++++++DMESG OUTPUT++++++++++++++++
[   38.614545] audit(1249433540.606:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4966 profile="/usr/sbin/cupsd" namespace="default"
[   78.383234] Marking TSC unstable due to: cpufreq changes.
[   78.391002] Time: acpi_pm clocksource has been installed.
[   78.630834] Clocksource tsc unstable (delta = -123972925 ns)
[   80.093907] Bluetooth: Core ver 2.11
[   80.094824] NET: Registered protocol family 31
[   80.094831] Bluetooth: HCI device and connection manager initialized
[   80.094839] Bluetooth: HCI socket layer initialized
[   80.161290] Bluetooth: L2CAP ver 2.9
[   80.161301] Bluetooth: L2CAP socket layer initialized
[   80.220999] Bluetooth: RFCOMM socket layer initialized
[   80.221029] Bluetooth: RFCOMM TTY layer initialized
[   80.221033] Bluetooth: RFCOMM ver 1.8
[   82.924773] 0000:04:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   82.924790] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   83.438899] NET: Registered protocol family 17
[   45.761698] NET: Registered protocol family 10
[   45.761921] lo: Disabled Privacy Extensions
[   45.763137] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  104.167125] eth0: no IPv6 routers present

+++++++++++++++++END OF DMESG OUTPUT+++++++++++++++

++++++++++++++++LSMOD OUTPUT+++++++++++++++++++++
Module                  Size  Used by
ipv6                  268036  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
snd_hda_intel         346136  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
evdev                  13056  3 
dcdbas                  9504  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
psmouse                40336  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
button                  9232  0 
nvidia               7825536  24 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2             7680  0 
agpgart                34760  1 nvidia
k8temp                  6656  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
i2c_core               24832  2 nvidia,i2c_nforce2
soundcore               8800  1 snd
ext3                  136968  6 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  8 
pata_acpi               8320  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
sata_nv                27656  7 
b44                    28560  0 
ata_generic             8324  0 
ssb                    34308  1 b44
mii                     6400  1 b44
tulip                  53664  0 
ehci_hcd               37900  0 
ohci_hcd               26640  0 
libata                159728  3 pata_acpi,sata_nv,ata_generic
scsi_mod              151692  4 sg,sr_mod,sd_mod,libata
usbcore               146412  4 usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36616  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
+++++++++++++++END OF LSMOD OUTPUT+++++++++++++

+++++++++++++++LSUSB OUTPUT+++++++++++++++++++

Bus 001 Device 003: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1241 Belkin
  idProduct          0x1166 optical mouse w/ scrollwheel
  bcdDevice            2.70
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)
++++++++++++++END OF LSUSB OUTPUT++++++++++++

Ok, hanging tight here. :)

---

### Post by loctavius on 2009-08-05
> **afrodeity said:**
> Please post contents of dmesg | tail we can troubleshoot from there!

Here is the output of dmesg | tail -20 after the mouse froze again. And trying to exit to the login screen after the mouse froze locked up the entire screen, keyboard and all, it froze the system. So I can't go back to the welcome screen like finch suggested to see if it is just X Windows or not.


Bus 001 Device 003: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1241 Belkin
  idProduct          0x1166 optical mouse w/ scrollwheel
  bcdDevice            2.70
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

---

### Post by finch127 on 2009-08-05
Hey uh the last post wasn't dmesg it was lsusb after the mouse froze. You mind trying again? If you wish what you can do is run the command and append "> out.txt" to the end to get a nice text file you can upload so you dont have to retype it all after you freeze.

Also, quick question, when you said that everything locked up, what keypress combo did you use? Was it ctrl+alt+backspace or the trick to where you got to another terminal using ctrl+alt+F2 etc? Because if it was the first one and everything locked up, I am betting on X Windows being busted here. The dmesg and lsmod output you posted looks pretty normal to me, as well as the lsusb... the only thing we can't really check like that is X Windows. I am still a little unsure though, afrodeity what do you think?

---

### Post by finch127 on 2009-08-05
Oh yeah, @ afrodeity, his keyboard still works when his mouse goes, and remember it is USB as well so it may not be the USB module.

---

### Post by loctavius on 2009-08-05
> **finch127 said:**
> Hey uh the last post wasn't dmesg it was lsusb after the mouse froze. You mind trying again? 

I posted the wrong file by mistake. This is the dmesg file after it froze. And yeah, I've been piping the output to text files so I don't have to type it out since you reminded me how. :) Thanks for that.

So you should be able to compare this dmesg output to the one I posted a little bit ago.

I don't remember which keyboard combination broke it - I'll try it again and let you know.

[   78.383234] Marking TSC unstable due to: cpufreq changes.
[   78.391002] Time: acpi_pm clocksource has been installed.
[   78.630834] Clocksource tsc unstable (delta = -123972925 ns)
[   80.093907] Bluetooth: Core ver 2.11
[   80.094824] NET: Registered protocol family 31
[   80.094831] Bluetooth: HCI device and connection manager initialized
[   80.094839] Bluetooth: HCI socket layer initialized
[   80.161290] Bluetooth: L2CAP ver 2.9
[   80.161301] Bluetooth: L2CAP socket layer initialized
[   80.220999] Bluetooth: RFCOMM socket layer initialized
[   80.221029] Bluetooth: RFCOMM TTY layer initialized
[   80.221033] Bluetooth: RFCOMM ver 1.8
[   82.924773] 0000:04:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   82.924790] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   83.438899] NET: Registered protocol family 17
[   45.761698] NET: Registered protocol family 10
[   45.761921] lo: Disabled Privacy Extensions
[   45.763137] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  104.167125] eth0: no IPv6 routers present
[30109.989843] sr0: CDROM not ready.  Make sure there is a disc in the drive.

---

### Post by finch127 on 2009-08-05
yeah I still dont see anything wrong in the dmesg trail, everything seems fine you know.

---

### Post by loctavius on 2009-08-05
> **finch127 said:**
> yeah I still dont see anything wrong in the dmesg trail, everything seems fine you know.

Ok, next couple of ideas? You threw a lot at me overnight in a few posts, and I'm lost as to what I've done and what I haven't. :)

---

### Post by finch127 on 2009-08-05
Well have you found which key combo locks you out and which one didnt? That may help a little.

Further, try this:

Go to the main ubuntu download site, and download the newest 9.04 cd (latest build). Try it out in live mode and see if your mouse freezes in live mode.

---

### Post by loctavius on 2009-08-05
> **finch127 said:**
> Well have you found which key combo locks you out and which one didnt? That may help a little.

Further, try this:

Go to the main ubuntu download site, and download the newest 9.04 cd (latest build). Try it out in live mode and see if your mouse freezes in live mode.

Can you explain to me what live mode is and how to use it? I've never done that before.

---

### Post by finch127 on 2009-08-06
Yeah, basically you download the ISO image from the website, and burn it to a CD like normal. You stick it in the drive and let it boot from CD (I assume you know how to do this because you installed Ubuntu). Then it comes up with a menu asking you for language, just hit english and the options come up. just hit, "Try Ubuntu without any Change to my Computer" and let it boot from CD until you get a trial desktop. You can go ahead and see if the mouse works in the Live Cd mode and come back here when you wish. If it does work, I recommend upgrading to 9.04 because I know for myself, my laptops graphics card suddenly fixed itself on that new install of 9.04 (jaunty jackalope). Also its faster :p so you may want to do it anyway. 9.10 comes out in 2 months so maybe if 9.04 doesnt work for this, you can also try the 9.10 live CD when its stable and released? idk but just stick to this test for now.

---

### Post by loctavius on 2009-08-06
> **finch127 said:**
> Yeah, basically you download the ISO image from the website, and burn it to a CD like normal. You stick it in the drive and let it boot from CD (I assume you know how to do this because you installed Ubuntu). Then it comes up with a menu asking you for language, just hit english and the options come up. just hit, "Try Ubuntu without any Change to my Computer" and let it boot from CD until you get a trial desktop. You can go ahead and see if the mouse works in the Live Cd mode and come back here when you wish. If it does work, I recommend upgrading to 9.04 because I know for myself, my laptops graphics card suddenly fixed itself on that new install of 9.04 (jaunty jackalope). Also its faster :p so you may want to do it anyway. 9.10 comes out in 2 months so maybe if 9.04 doesnt work for this, you can also try the 9.10 live CD when its stable and released? idk but just stick to this test for now.

Man that is soooooo cool. I'll do it, as well as the keyboard things you wanted me to try.

---

### Post by loctavius on 2009-08-06
> **finch127 said:**
> Well have you found which key combo locks you out and which one didnt? That may help a little.


Ok, toda's Great Mouse Adventure is on tap.

Mouse freezes. I tried plugging in another USB mouse as suggested in an earlier post. The new mouse made the mouse cursor move for about 2 seconds, then it too froze.

Tried using CTRL+ALT+F2 as suggested earlier, and the entire computer borked. Had to pull the power cored to fix it.

Rebooted by pulling power. Used the computer, mouse froze. 

Tried CTRL+ALT+BACKSPACE. Did not work. It started to exit, then froze with only the wallpaper showing. All windows and other items were gone. System appeared to be frozen. Attempted the ALT+PRINT SCREEN R E I S U B just for kicks, but it had no effect either.

So since all the key combinations failed, do you want me to try the Live CD thing next?

---

### Post by afrodeity on 2009-08-06
Yes,loctavious. You need to eliminate the possiblity that its a hardware error.

Boot from LiveCD and use a live session. If mouse works fine, then there's a problem with the software, in all likelihood the kernal module, which is why I suggest unloading and reloading psmouse ([as per my post]("http://ubuntuforums.org/showthread.php?t=1231333"))

I can't see much wrong in the dmsg, which means you haven't managed to catch the bug while its being logged. I was just lucky to catch mine, so no luck there.

You could also try the beta of Karma, the Ubuntu beta's are usually pretty good.

Will take another look at what you've posted. Sorry wasn't around earlier, hectic day today.

Will check in again tomorrow SA time.

---

### Post by afrodeity on 2009-08-06
Okay I took another look at your dmsg output and see that it reports the following problem: 
```

[ 82.924773] 0000:04:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
```

which is an ethernet card/networking bug related to: 
[URL="https://launchpad.net/ubuntu/+source/udev/+bug/48026"]
https://launchpad.net/ubuntu/+source/udev/+bug/48026[/URL]

and

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/48287]("https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/48287")


To remedy bug, it is suggested to:
rmmod tulip
rmmod dmfe
modprobe dmfe

 followed by:

/etc/init.d/networking stop
/etc/init.d/networking start

if rmmod doesn't work, try modprobe -r, you probably also need to use the sudo command to get anything to work.

For the life of me, I don't see why this should affect your mouse, but its worth doing it, just to eliminate the freaking possibility that your kernal is loading the wrong driver for your ethernet card and this is somehow resulting in X and your keyboard freezing up.

Sorry I can't be of more assistance.

---

### Post by loctavius on 2009-08-06
> **afrodeity said:**
> Okay I took another look at your dmsg output and see that it reports the following problem: 
```

[ 82.924773] 0000:04:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
```which is an ethernet card/networking bug related to: 
[URL="https://launchpad.net/ubuntu/+source/udev/+bug/48026"]
https://launchpad.net/ubuntu/+source/udev/+bug/48026[/URL]

and

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/48287](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/48287)


To remedy bug, it is suggested to:
rmmod tulip
rmmod dmfe
modprobe dmfe

 followed by:

/etc/init.d/networking stop
/etc/init.d/networking start

if rmmod doesn't work, try modprobe -r, you probably also need to use the sudo command to get anything to work.

For the life of me, I don't see why this should affect your mouse, but its worth doing it, just to eliminate the freaking possibility that your kernal is loading the wrong driver for your ethernet card and this is somehow resulting in X and your keyboard freezing up.

Sorry I can't be of more assistance.

Don't apologize - free help is better than no help, even if you and finch aren't sure what the problem is, so I'm thrilled to have it!

I'll give all this a shot tomorrow morning then. Gotta be up early anyway.

For the record, the network on the Ubuntu box seems to work fine, if a tad slow from time to time when loading a webpage or something. But the LAN portion works great (it is a great Samba server), and I can get online OK with it. But I'll do all that (and the Live CD) just to try it anyway.

---

### Post by finch127 on 2009-08-06
Alright I got one more idea:

```

sudo service gdm stop
sudo service gdm start

```

OK when your mouse is blocked up, have your terminal ready, and try those two commands. You should be ejected to your login and try and log back in to see if the mouse restarts.

---

### Post by finch127 on 2009-08-11
Hey loctavius, did any of this work for you?

---

