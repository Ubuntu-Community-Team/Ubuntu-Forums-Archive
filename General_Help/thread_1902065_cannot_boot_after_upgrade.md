---
title: "cannot boot after upgrade"
date: 2011-12-29
forum: General Help
---

### Post by galaxyaurona on 2011-12-29
Hi guys, I'm new with ubuntu so please help me. I can't do nothing now. Here is my story

I was on ubuntu 10.4 yesterday , then the OS ask me to upgrade some important file.The process ran smoothly. Then it asked me to restart to complete update. After I restarted ,the screen went black although the power still on. 

After a while ,i accidentally hit the reset button. It automatically turn on again but the screen is still black. I tried press the power button foi 10 seconds but it continue to turn on on it own. The only option is to removed the power. 

To sum up, now , when i turn the laptop on, it only show black screen, no logo ,no boot option, cannot boot into boot able disk. It will automatically turn on unless you remove the power. 

Can someone please help me.I really need my computer right now. And sorry for my bad english too.

---

### Post by galaxyaurona on 2011-12-30
Please help me, I'm in need for my laptop. My bios is still working cuz I can still fell the warm, but It cannot boot livecd or respond . and I don't know how to install GRUB since I can't get access to anything.

---

### Post by Buggrit on 2011-12-30
hi, I'll do my best to help. 

do you see the black and white CMOS screen when you boot? usually this gives information about the hard disks, RAM, BIOS etc.

---

### Post by galaxyaurona on 2011-12-30
thank you, finally one respond.
To be honest, when I turn my laptop on ,it only show a black screen, the led indicate power is on, there is heat at the fan ,but that is all of it.

---

### Post by chipbuster on 2011-12-30
That's, uh.....not good. At all.

Does the screen doesn't power up and show black?

---

### Post by nothingspecial on 2011-12-30
Do you have a brightness or turn the screen on/off button on your laptop? One of my laptops boots with the screen turned off. I have to press F3 to switch it on.

---

### Post by guestolo on 2011-12-30
In addition to nothingspecial suggestion
Have had this work in the past on anothers laptop
Not exactly same circumstances

Remove power cord from laptop
Remove Battery from laptop
Hold down power button for around 30 seconds
Reattach power cable and try to boot computer

If it boots, shut down, put the battery back in and again try to boot without power cable this time
Assuming that battery has charge

---

### Post by galaxyaurona on 2011-12-30
Thank you so much guys

I tried all of the method you suggested,but none of them worked

It seems like my screen is off black and I'm pretty sure I tried to turn it on and increase the brightness
Plus, my Asus k43s have a unique startup logo and sounds before I can go to Bios setting or boot manager,but now I can't hear anything.It's like it cannot start at all, but the CPU still running ,and I can open my DVD drive too

---

### Post by guyver_dio on 2011-12-30
So you're not even seeing a bios screen? The very first thing you should see when you turn the computer on before it even starts trying to boot anything? 

If that is true I hope it's still under warranty because I would be seriously thinking hardware problem. Not trying to say it's not ubuntu's fault or the fault of the upgrade you did but I struggle to see any OS upgrade doing anything like that. Unless you actually flashed your bios on purpose an OS wouldn't touch it. 

If this were a desktop I'd probably suggest reseating the ram but that's pretty uncommon with laptops (at least I've never come across it), but give it a go if you like.

---

### Post by galaxyaurona on 2011-12-30
I hope it is not a hardware problem because no one would fix my laptop at this time of the year.

My laptop is running on both win7 and Ubuntu. Last time I used Ubuntu and these is no sign of serious hardware problem. 

I know it sounds crazy but I if because I interrupted its upgrading after restart so now it's trying to complete or not. It automatically turn on when I pressed power for 10s

---

### Post by mörgæs on 2011-12-30
The best test for examining hardware problems is a live boot. How does this work?

---

### Post by galaxyaurona on 2011-12-30
Not good, I put live CD in and restart but the screen is still black

---

### Post by Buggrit on 2011-12-30
> **galaxyaurona said:**
> Not good, I put live CD in and restart but the screen is still black

The screen will be black because the computer first starts out as a Box-of-rocks and then gets its initial instructions (known as the BIOS), from a chip which is hard-wired onto the motherboard. After that the BIOS tells the hardware what it is and how to become a basic computer and only then does the machine look around for a proper operating system such as Windows or Linux.

Your problem is happening before the BIOS has had a chance to hand-off to the Operating system, therefore the operating  system cannot be the problem and what you are experiencing must be a hardware problem.

Things to do...
1.) Check the lid-switch is not stuck down as that can cause he machine to think it is still closed and so it won't boot. The switch usually looks like a little spike somewhere near the screen hinges. 

2.) The back-light may have shorted, which means the screen may be showing all the normal stuff but you can't see it because there is zero lighting. Check for this in 2 ways..,
* firstly get a torch and shine it against the screen at various angles to see if there is any writing or images. If you do see images then you know it is the backlight and you will probably need to replace the "Screen Inverter"
* Secondly If you can get hold of a screen or tv monitor, plug it in to the video port on the laptop and hit the appropriate function key to send the video signal to the screen. If the screen lights up then you know your laptop's internal screen is broken and will probably need replacing. If the screen does not respond, then you know the problem probably lies on the motherboard, Memory or CPU and further testing will be needed to ascertain exactly which one is at fault.

I hope this helps. Unfortunately I have to go now and will be off line for a while so I'll leave you in everyone else's capable hands...

JB

---

