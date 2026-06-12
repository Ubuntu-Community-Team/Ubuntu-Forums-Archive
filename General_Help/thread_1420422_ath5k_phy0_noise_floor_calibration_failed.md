---
title: "ath5k phy0: noise floor calibration failed"
date: 2010-03-03
forum: General Help
---

### Post by solorize on 2010-03-03
Hi have Ubuntu 9.10 but am having a problem when my laptop boots up.
Just before it gets to the circular loading graphic it just hangs, I have waited
a while but it does not seem to get any further.

So I turn the power off and try again, but this time I get the GRUB boot
loader come up so I decided to choose the “Recovery” option, this then displays the
lines of text regarding what’s loading etc.. then it sits there for a while.

It then displays a menu saying something like “boot as normal” and some other
options, but I cant see what they are as the following message comes up
over the top of it:

**[  312.287094] ath5k phy0: noise floor calibration failed (5785MHz)**

Then every couple of  seconds another line as above appears with a different number between the **[    ]** brackets.

Does anyone know what this is? and if this would be causing the problem when trying to boot up
when it just hangs. 

I have been looking on google and it seems that it may be something to do with the WiFi,
but as I am new to Linux I am not 100% sure what it is and how it may be affecting the system.

If anyone can shed any light on this matter I would be grateful.

Regards

Mark

---

### Post by solorize on 2010-03-06
Think I have worked out what is causing the problem. My video sender for my TV
(sending Sky from downstairs to the tv in my bedroom), works on the following frequencies:

(channel 1) = **5745Mhz**
(channel 2) = **5765Mhz**
(channel 3) = **5785Mhz**
(channel 4) = **5805Mhz.**


So when I look at my DMESG.LOG I can see the Noise floor calibration errors changing to which
ever frequency I change the Video sender to.

The snippet of my DMESG.LOG file below shows in the 1st part
the frequencies that my wireless card uses, as you can see
the **BOLD** frequencies are right where my Video Senders
frequencies are.

Also the last part below shows the "noise floor calibration"
fails for the frequencies as I change through the 4 available
frequency channels that I have on my video sender.

[COLOR="Red"]----snippet of DMESG.LOG-----[/COLOR]

[I][ 48.074614] (start_freq - end_freq @ bandwidth), max_antenna_gain, max_eirp) 
[ 48.074619] (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,2000 mBm) 
[ 48.074623] (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi,2000 mBm) 
[ 48.074627] (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi,2000 mBm) 
[ 48.074631] (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi,2000 mBm) 
[ 48.074635] (**5735000 KHz - 5835000** KHz @ 40000 KHz),(300 mBi,2000 mBm) 
.
.
.
.
[ 663.295601] ath5k phy0: noise floor calibration failed (**5745MHz**) 
[ 783.603538] ath5k phy0: noise floor calibration failed (**5765MHz**) 
[ 1024.167787] ath5k phy0: noise floor calibration failed (**5785MHz**) 
[ 1264.591521] ath5k phy0: noise floor calibration failed (**5805MHz**) [/I]


[COLOR="Red"]----snippet of DMESG.LOG-----[/COLOR]


I guess I will have to turn off the Video senders everytime I boot up the laptop, wait until I am into the OS and then turn them back on.

Unless there is a way I can stop the wireless card in the Laptop from using a specified range of frequencies?
Does anyone know if this is possible and can tell
me how to do this.

Regards

Mark

---

