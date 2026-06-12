---
title: "Digital Camera / dvgrab &quot;Error: no camera exists&quot;"
date: 2006-05-12
forum: General Help
---

### Post by aq404 on 2006-05-12
Hi,

About 2 months ago everything was work. I was grab films from camera without problems. That mean that probally all settings i have correct. I find on this forum and anothers that maybe i have wrong kernel. But i not change only when automatic updater want. Aha and i add USB PCI Card.. maybe that? but Firewire its in the same place in computer;)

My error:
$ dvgrab -i
```
"Error: no camera exists"
```

My actuall kernel is: ** 2.6.12-10-k7**
I was try also kernal from ubuntu: ** 2.6.12-9-k7**
and from kernel.org: **2.6.16.9**

Some informations:
```
$ testlibraw 
successfully got handle 
current generation number: 1 
1 card(s) found 
  nodes on bus:  0, card name: ohci1394 
using first card found: 0 nodes on bus, local ID is 0, IRM is 63 

doing transactions with custom tag handler 

using standard tag handler and synchronous calls 

testing FCP monitoring on local node 
testing config rom stuff 
get_config_rom returned 0, romsize 120, rom_version 3 
here are the first 10 quadlets: 
0. quadlet: 0xd6470404 
1. quadlet: 0x34393331 
2. quadlet: 0x32a264e0 
3. quadlet: 0x024c0000 
4. quadlet: 0xd49b0108 
5. quadlet: 0x05390400 
6. quadlet: 0x4c000003 
7. quadlet: 0x03000081 
8. quadlet: 0x090000d1 
9. quadlet: 0xc083000c 
update_config_rom returned 0 

polling for leftover messages
```

```
$ sudo lshw | grep 1394 
                description: FireWire (IEEE 1394) 
                product: IEEE 1394 Host Controller 
                configuration: driver=ohci1394
```

```
$ lsmod | grep 1394 
video1394              19852  0 
ohci1394               34804  1 video1394 
raw1394                29548  0 
ieee1394              101752  4 video1394,ohci1394,raw1394,sbp2
```

```
$ ls -l /dev/raw1394 
crw-rw-rw-  1 root video 171, 0 2006-05-11 17:06 /dev/raw1394 

```

```
 
$ lspci 
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1) 
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1) 
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1) 
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1) 
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1) 
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1) 
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4) 
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2) 
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1) 
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1) 
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) 
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) 
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) 
0000:01:08.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
0000:01:08.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
0000:01:08.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
0000:01:08.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) 
0000:01:09.0 FireWire (IEEE 1394): NEC Corporation IEEE 1394 Host Controller (rev 01) 
0000:02:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01) 
0000:02:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
```

Can someone help? Maybe some tips?

Greetings
Lukasz
AQ

---

### Post by Zorb on 2006-05-21
I'd love to help, but I'm having the same problem myself! As all tech support loves to hear, "It was working last time I tried it!"

Seriously, it just stopped working.

---

### Post by sascha on 2006-06-18
I am having the same issue too..............please can anyone help?

---

### Post by ronb on 2006-06-23
This is probably obvious and won't help but just in case...

I got the 'no camera exists' message when the camera was turned off. It needs to be in VCR mode.

Also, following the advice in another thread, I did a chmod 777 /dev/raw1394, and I did a chown to my user id.

---

### Post by Blenderdan on 2007-06-17
Did anyone ever figure out how to fix this problem?

I am having pretty much the exact same issue.  I have a Gateway 8510GZ Notebook with a built in fire wire port. 

This is my first attempt to capture video with this firewire port.  raw1394 was not in my /dev directory so I had to enter "modprobe raw1394"  which made it show up.  I than tried the suggestions posted here before my post.  Chmod 777 /dev/raw1394 and chown userid:video /dev/raw1394.

Still the same problem.  dvgrab says "Error: no camera exists" and kino just doesn't see my camera.

This is a year after the last post in this thread, is there any solutions yet?

thanks

---

### Post by CescoAiel on 2007-07-25
Got the same issue....

I have raw1394 and dv1394 loaded, the devices exist, testlibraw finds the hardware (as above) but dvgrab and kino do not see a camera...

I am using a VIA DV card and a Sony PC120 camera...

Even tried 'gksudo kino'...

The only 1394 related message I saw on kino was this one:
>>> dv1394Writer::dv1394Writer /dev/dv1394/0 channel 63 fd -1

[SIZE="6"][COLOR="Red"]HELP!!!!![/COLOR][/SIZE]

[EDIT:] Just tried same camera and cable on a MacOS/X machine, where it all worked fine, so cable and camera are ok!...

---

### Post by brunomalone on 2007-09-26
Same problem here.  Any help will be very welcome.

---

### Post by jmiter on 2008-01-19
I ran into this problem today as well

Kino not recognizing my video camera
dvgrab says no camera exists
and this worked fine months ago when I last dumped video off of my camera.

Searchng google did not produce to many useful hits.  I've noticed when you are experiencing an appearently long standing problem and there are not many other people experiencing the same problem - the issue is likely with your own setup

So to fix the problem and something others may want to look at on their own system...
1. I did make sure the ieee1394 modules we entered into /etc/modules:
# 1394 for kino
ieee1394
dv1394
video1394
raw1394
ohci1394

(Not sure if I really need them or not, but hey - the camera is working now)

2. Initially after installing the modules - camera still did not work.  I changed permissions on all the /dev/ files related to 1394 - no luck.

3. Finally - I looked at the motherboard where my 1394 is plugged in.  I have 2 motherboard connectors for my 1394 as I have a connection on the front of my computer.  I changed to the second connector, which was not being used, tested with dvgrab - and itworked.  Kino is capturing fine as well.

running ubuntu gutsy 7.10
2.6.22-14-generic amd64 bit, 3700+

---

### Post by crack on 2008-02-09
i have similar problem, i bought the firewire card with via vt6306 chipset and added it to pci slot:


lspci:
```
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. Unknown device 2044 (rev 46)

```

sudo lshw | grep 1394 :
```

~$ sudo lshw | grep 1394 
          capabilities: apm int13floppytoshiba acpi usb ieee1394boot biosbootspecification
             description: FireWire (IEEE 1394)
             configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
```

dvgrab doesn't detect camera same as kino, i tried starting the modules mentioned in post above, and connecting my camera to all three ports available on firewire card but nothing has changed, kino still cant see my handycam (sony dcr-hc46)

---

### Post by jumpinbeanfever on 2008-02-11
I had this same problem. Try going into your camera's set-up menu and changing the USB Connect setting to PTP.

It worked for me.

---

### Post by Baromur on 2008-04-18
I have a samsung DV cam. I got the same problems. I loaded all the modules changed the permissions but nothing happened. I tried to switch off the camera or pull out the cable from the computer the result is the same. But when I tried to pull out the cable from the camera and and push back the av/c started to work!!!
So when I want to grab my videos than the last step what I do that I push the cable into the camera.
Unbelieveable....

---

### Post by chris-man on 2008-05-07
Well I was experiencing exactly the same problems with my JVC GR-DX57

The two (and a half) things I did which suddenly made it jump into life and work with Kino / dvgrab were:

1. In my /etc/modules file I've only loaded raw1394 and ohci1394
2. Unplug my firewire card from my pc and try a different PCI slot
(2 1/2. Blow the dust off the connectors)

After a reboot I noticed when I plugged my camcorder in, dmesg showed a change, which it previously didn't, and then Kino recognised my camcorder.

I hope this helps someone else as I've spent a good 2-3 hours working on this!

Chris

---

