---
title: "No Internet On Mum's Computer (Ubuntu 8.04)"
date: 2011-11-20
forum: General Help
---

### Post by Spice Girls on 2011-11-20
I just installed Ubuntu 8.04 becuase Lubuntu didn't work out, too limited witht he GUI and customizations.

I got Ubuntu 8.04 installed, but there is no internet, even connected to LAN. There dosen't seem to be a spot for the wireless internet.

---

### Post by roger_1960 on 2011-11-20
Hi

Why are you trying to install an old now unsupported version?  Suggest you try 10.04LTS if you want something with the bugs sorted out. (although 8.04 was OK as I remember)

With the current installation, can you post the output from

> ifconfig

from terminal?

What type of computer is it?  Have you checked the settings in the network dropdown at the top right of the screen?

---

### Post by Spice Girls on 2011-11-20
ipconfig says "command not found".

The laptop is a Toshiba Satellite 655D (2010-2011). My Mum got it in the US while she was visiting. I am installing an older version of Ubuntu because it only has a 1GHz processor and the current versions don't work well, they lag a lot. Someone told me to install an older version.

I've tried 11.04 and I think 10.10 but it's not recommended for a low end processor.

---

### Post by mikewhatever on 2011-11-20
...but it's not ip..., it's if... :~)

---

### Post by roger_1960 on 2011-11-20
Hi again

Yes

> ifconfig

I had a look at that laptop and it appears to have a really good spec.  Shouldn't have any trouble with 10.04LTS.  The issue is that (once you have internet working) you won't get any online updates with 8.04 but 10.04 is supported until april 2013 with security updates etc.

---

### Post by Sylslay on 2011-11-20
Well.
I instaled 10.04 on p3 800MHZ and p3 IBM thinkpad with 1000MHz, 
it was faser than on 2.5 GHZ celeron in Siemens lapotp.

Recomended 10.04

---

### Post by egalvan on 2011-11-20
> **Spice Girls said:**
> [COLOR="Red"]ip[/COLOR]config says "command not found".

it should be [COLOR="Red"]if[/COLOR]config


> The laptop is a Toshiba Satellite 655D (2010-2011). My Mum got it in the US while she was visiting. I am installing an older version of Ubuntu because **it only has a 1GHz processor** and the current versions don't work well, they lag a lot. Someone told me to install an older version.

I've tried 11.04 and I think 10.10 but it's not recommended for a low end processor.

it really depends on how much RAM you have installed.
I'm running 11.04 on an older Thinkpad T40, which has a 1.3MHz CPU,
 but is maxed out at 2Gb RAM.
it runs fairly well.

I had started with 10.04LTS, but upgraded to 11.04 mainly for the hardware support (wireless and broadband)

---

### Post by Spice Girls on 2011-11-21
It has 3GB of DDR3 memory.

I found a USB wireless stick, it dosen'[t work but the wierd thing is. if I goto ifconfig, it will detect it becuase the wlan shows up, but if I remove it, it will only say lo even though the laptop has a built in wireless card and it work before installing Ubuntu 8.04.

Here is the info for ifconfig:
> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11368 (11.1 KB)  TX bytes:11368 (11.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:a3:05:03:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1260 (1.2 KB)


---

### Post by bkratz on 2011-11-21
If you post the output of:


lspci -nnk | grep -iA2 net

We can get a complete look at your internal wireless and wired card. By the way that was LSPCI in lowercase. The | is just above the enter key on a US keyboard.

---

### Post by snowpine on 2011-11-21
Don't worry about typos or where the keys are on your keyboard; just Copy and Paste for accuracy...

Check for these obvious things: Is there a physical switch that turns wireless on/off? Is there a keyboard combination to turn wireless on/off? Are there any settings in the BIOS (accessed when you first turn on the computer by pressing a certain key) to turn wireless on/off? 

This is in addition to bkratz's command above, which you should copy & paste the output of.

Alternately you could simply test-drive a Live CD/USB of the current release. The wireless hardware might "just work" in the new release.

---

### Post by Spice Girls on 2011-11-21
I get:

> lspci: invaled option - - k
Usage: lspci [<switches>]

---

### Post by Spice Girls on 2011-11-21
UPDATE: I got Internet, however it will only work on the USB wireless stick. I will try and do updates and update the Kernel. It needs Graphics LAN/WLAN drivers, hopefully the Kernel will fix that.

---

### Post by bkratz on 2011-11-21
> **Spice Girls said:**
> UPDATE: I got Internet, however it will only work on the USB wireless stick. I will try and do updates and update the Kernel. It needs Graphics LAN/WLAN drivers, hopefully the Kernel will fix that.

Glad to hear you are making progress. Just out of curiosity I did an 
man lspci and found the following



```
 -k     Show kernel drivers handling each device and also kernel modules
              capable of handling it.  Turned on by default when -v  is  given
              in  the  normal  mode of output.  (Currently works only on Linux
              with [COLOR="Red"]kernel 2.6[/COLOR] or newer.)
```


Do you know what the kernel is in the version you are using?
You can find out with

```
uname -r
```

---

### Post by Spice Girls on 2011-11-21
I did  updates and now are Kernel: 2.6.24-30-generic.

The updates didn't do anything for drivers, I still can only access Internet via the USB stick.

---

### Post by bkratz on 2011-11-21
> **Spice Girls said:**
> I did  updates and now are Kernel: 2.6.24-30-generic.

The updates didn't do anything for drivers, I still can only access Internet via the USB stick.



Does the earlier command work now? If not, we can probably get the information on the wireless with

```
lspci -nn | grep 0280
```

If we can't get it there we can always just do an lspci -nn and copy the info the hard way (with a pencil or copy/paste)!

---

### Post by Spice Girls on 2011-11-21
Too many problems with 8.04, going to try 9.04 I think. It's too obsolete that even fetching data from Synaptic Manager won't work.

---

### Post by bkratz on 2011-11-21
> **Spice Girls said:**
> Too many problems with 8.04, going to try 9.04 I think. It's too obsolete that even fetching data from Synaptic Manager won't work.



I loved 9.04 it was the best, but it is obsolete too!

---

### Post by snowpine on 2011-11-21
> **Spice Girls said:**
> Too many problems with 8.04, going to try 9.04 I think. It's too obsolete that even fetching data from Synaptic Manager won't work.

9.04 = April 2009

The current release is 11.10 (October 2011)

---

