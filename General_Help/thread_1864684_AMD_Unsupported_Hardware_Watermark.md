---
title: "AMD Unsupported Hardware Watermark"
date: 2011-10-19
forum: General Help
---

### Post by Turbo556 on 2011-10-19
Hey all,

I just recently installed 11.10 Ubuntu Ocelot and I have tried several work arounds to fix this watermark and can't.....It will let me install the basic driver package in (jockey) but not the updated one...it gives me a jockey error when I do that....regardless the WM is still there...

I have a ATI Radeon 3870x2, AMD 6 core processor, and 4 gb of ripjaws RAM.....

How do I fix this watermark and make sure I have the most up to date and best drivers/CCC?

Thanks in advance....

---

### Post by Blaqksheep on 2011-10-19
Replace that Thuban hexacore with a processor that actually gets decent benchmarks!  If that thing were any more overrated it'd be the Twilight Movie in 45nm form.

If I had to venture a guess, it would be those old 3000 series GPUs that are giving you fits.  AMD bought ATI a while back and they might not like old ATI cards like that.  How are you trying to update the drivers?  Maybe trying it a different way will work better for you.  If not, does the motherboard that old Thuban is plugged into have an integrated GPU?  If so, pull the crossfired GPUs out and see what happens.  Can you do the upgrades with them removed?  If you just can't seem to get it to work, you might just want to replace them.  You can pick up an AMD HD 6670 from Newegg for ~$80 which has a higher benchmark than your crossfired 3870s.

I'll go ahead and tell you, if you're in the market to upgrade those parts, go ahead and play the waiting game.  AMD Radeon HD 7000 GPUs, Intel Ivy Bridge processors, and DDR4 RAM are dropping 2012ish.  That's not even including Ubuntu 12.04 LTS and the vaunted Windows 8.  =)

---

### Post by Turbo556 on 2011-10-19
I did a benchmark on my processor a few months back man and with mine overclocked it was just a few pints below an i7 extreme if I remember correctly.....very fast...

The motherboard has no onboard graphics....just so you know the 3870 x2 is not two 3870 cards...it this:  [http://www.anandtech.com/show/2428](http://www.anandtech.com/show/2428)

Frankly I haven't replaced it cause it takes everything I can throw at it....BBC2 on the highest settings, MW2 on the highest settings...its a real work horse of a card....

I have been trying to update it via the additional drivers...the first ATI goes through but the second one gives me that jockey error and wont take regardless if I do it through Addtl Drivers or through the terminal....I have also tried doing it for my card through AMD's site...when I reboot I get the black screen after login or a white screen with lines....it didn't work....

How do I fix this?

---

### Post by Turbo556 on 2011-10-19
Anyone>?

---

### Post by homerhomer on 2011-10-20
Yes, I had the same issue. Here's script to fix it. Works for me.  Just run in terminal with root permissions and log out and then reboot. You should be good.

---

### Post by Turbo556 on 2011-10-20
Is that a script to just remove the Watermark?  Although that is helpful...what I am really looking to do is have the proper drivers installed so my video card works optimally and the watermark goes away on its own.....

---

### Post by dburgan on 2011-10-20
> **homerhomer said:**
> Yes, I had the same issue. Here's script to fix it. Works for me.  Just run in terminal with root permissions and log out and then reboot. You should be good.

This solved it for me. Although the idea of patching a critical .so file makes me feel dirty. :D  But thanks for a solution that finally made that infernal watermark go away.

It would be nice if ATI would provide a driver that didn't have such a bogus message in it. My video is running and performing great on this laptop, just as it did under Ubuntu 11.04.

Anyway thanks again ...

---

### Post by Turbo556 on 2011-10-20
Can anyone help me with these drivers so that I have the proper ones?

---

### Post by 2017 on 2011-10-21
> **homerhomer said:**
> Yes, I had the same issue. Here's script to fix it. Works for me. Just run in terminal with root permissions and log out and then reboot. You should be good.
How do I do this? I can get a terminal (alt Ctrl T) but then what?

---

### Post by dburgan on 2011-10-22
> **2017 said:**
> How do I do this? I can get a terminal (alt Ctrl T) but then what?

Download the script homerhomer provided, and in the terminal run the script under sudo. I strongly encourage you to back up the .so file it is patching first ... if it corrupts the .so file, you will probably not be able to get back into Ubuntu, so you'll want the option to be able to put it back again afterwards.

---

### Post by Turbo556 on 2011-10-22
Can anyone help with getting my proper drivers installed?

---

### Post by Turbo556 on 2011-10-22
Bump

---

### Post by homerhomer on 2011-10-22
Turbo556,

Hate to say it, but this is really just AMD/ATI dropping the ball. They are notorious and releasing bad, broken and messy drivers.  


 I installed the fglrx driver from there website and I also had the unsupported hardware issue.  Since the driver also has a suspend/hibernation bug as well, I stopped using and it and went with the open source radeon driver.

---

### Post by Turbo556 on 2011-10-25
How/where can I find an open source driver for the Radeon 3870x2 (note this is not two video cards its one with two gpus)?

---

### Post by mastablasta on 2011-10-25
the ones installed by default were opensource drivers. If they didnt' work then you are stuck with windows. if they did, then you can remove proprietary drivers and get the opensource ones back. instructions to do that can be found here: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by Turbo556 on 2011-10-29
Does anyone have a fix for me for this?

---

### Post by lightwarrior on 2011-10-29
Try the latest AMD/ATI drivers at AMD site.
Go to: [http://support.amd.com/la/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/la/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Download 11.9 Proprietary Display Driver and PDF install instructions.

(to install: just change file to executable and run with ./filename)

---

### Post by Turbo556 on 2011-10-29
Already tried through the AMD site...it wont boot....

---

### Post by Turbo556 on 2011-10-29
It just give me a screen that spazzes out with the drivers from the amd site...

---

### Post by oldtimer7777 on 2011-10-29
> **Turbo556 said:**
> Can anyone help with getting my proper drivers installed?

Script file above works great.. Did you try it?

---

### Post by Turbo556 on 2011-11-06
The4 script file just gets rid of the watermark....not puts in the right optimized drivers....am I correct?

---

### Post by dburgan on 2011-11-06
> **Turbo556 said:**
> The4 script file just gets rid of the watermark....not puts in the right optimized drivers....am I correct?

Yes, that is my understanding. It simply patches whatever driver is already there to remove the watermark image.

FWIW, last night I updated my Ubuntu 11.10 and a new fglrx driver came along for the ride. The watermark came back as a result, and I had to re-run this script to make the watermark go away. So whatever this problem is, the very latest driver from Ubuntu's repository still has the bug.

---

### Post by Steve_B_Welsh on 2011-11-07
Sorry to be the barer of bad news but as taken from the release notes on the AMD/ATI site:

> Note: The ATI RadeonTM HD 3870 X2 series of product is currently
not supported by the AMD Catalyst software suite for Linux.


This has been since that card was released and was the main reason I haven't taken up linux in the way i wanted to.

---

### Post by lighthouse-keeper on 2011-11-10
> **homerhomer said:**
> Yes, I had the same issue. Here's script to fix it. Works for me.  Just run in terminal with root permissions and log out and then reboot. You should be good.

Many thanks. This script worked perfectly for me to remove the watermark. I am using Ubuntu 10.10 on an Acer One 722 in case anyone else has this problem.

---

