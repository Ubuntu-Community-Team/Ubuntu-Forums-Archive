---
title: "Fan not running on laptop"
date: 2009-08-12
forum: General Help
---

### Post by Fox McCloud on 2009-08-12
Not sure if this is the right place to post, but I am having an issue with my fan not running.

Computer runs fine, but when I go to play WoW for about 3 mins, the display artifacts badly. 2D UI looks fine, just anything 3D. Second time it happened I noticed that the fan was not running. Normally, in Windows, the fan would be running at full blast.

I'm so close to getting rid of Windows, and this issue is holding me back...I need my WoW. O.o

I'll try to respond tonight...going to bed soon. :(

---

### Post by Tclarkie on 2009-08-12
so the fan still runs in windows

---

### Post by Tclarkie on 2009-08-12
which fan is it
 
this might help

---

### Post by gardara on 2009-08-12
Is the fan not running at all? Or just running at low rpm's?

---

### Post by madhavhmk on 2009-08-12
This is indeed a serious problem...!! :confused:

---

### Post by P4man on 2009-08-12
CPU or GPU fan?
Either way, definitely file a bug report on launchpad. and do not stress the machine by playing games or anything until you've found a solution. You'll damage your computer.

In the meanwhile, you might try getting around the problem by adding "noapic" and/or "nolapic" and/or "acpi=off" to your kernel parameters.

---

### Post by Fox McCloud on 2009-08-12
Whoa thanks for all the replies!

I think I have one fan, but no CPU fan. The fan in question for sure is over the GPU and runs slow at all times when running in Windows (I think that the CPU is being cooled some how from the GPU fan.) Though in Ubuntu I hear nothing.
> In the meanwhile, you might try getting around the problem by adding "noapic" and/or "nolapic" and/or "acpi=off" to your kernel parameters.I can't remember what I changed specially, but a few months ago I had modify my kernel so the sound would work correctly. I'll search for what it was, but I don't think it's the reason that the fan is not coming on.

---

### Post by Fox McCloud on 2009-08-12
I just looked on launchpad and found some one with a similar problem and tried this:```
sensors-detect
```

After some probing, it added this to my /etc/modules:```
# Chip drivers
coretemp
``` My question is, is there a way to determine that Ubuntu has control of my fan without running WoW to find out?

And one more thing, the fan does run, but the BIOS is set for it to run at all times. The fan just doesn't speed to up to what the load demands.

---

### Post by P4man on 2009-08-12
A few things; first, I cant believe you wouldn't have a cpu fan (unless its watercooled, or a 486 33 MHz CPU). That one fan you're seeing, is it on the mainboard, or on an add-in card ? 

If you only got one fan, its probably a cpu fan, and then you dont have a graphics card (because its integrated on the motherboard). OR you have a rare breed, a passively cooled graphics card. Double check to be sure. Follow your monitor cable, if it goes to an add in card, see if it doesnt have fans.

If its a gpu fan that is not speeding up, then it might be related to the videocard driver. If its the cpu fan, then when I wrote earlier about acpi definitely has an impact. Not saying that is your problem, or adding or removing it will solve it, but one of the many things ACPI does is powermanagement, including control fan speed.

Next, about the sensors thing; pretty easy. Install sensors-applet:

```
sudo apt-get install sensors-applet
```

The right click on the gnome panel (top or bottom), add to panel, and select the sensors applet. Right click it to configure it. It will only show whatever lm-sensors detected, but its worth a shot.

---

### Post by Onesimus on 2009-08-12
It might be helpful if you gave the specifications of the computer (e.g. make, model, etc. etc.) - this way solutions would be targeted for your hardware.

---

### Post by Fox McCloud on 2009-08-12
@P4man I installed the applet and it displays 5 sensors:

+libsensors
temp 1 30C/86F
core 0 32C/90F
core 1 32C/90F

+nivida
GPU 35C/95F

+acpi
CPU 30C/86F

> It might be helpful if you gave the specifications of the computer (e.g. make, model, etc. etc.) - this way solutions would be targeted for your hardware.Oops, that would be a good idea. :)
HP Pavilion dv7-1170US
CPU:Intel Core 2 Duo T5800 2.0Ghz
Memory:4GB DDR2
Graphics Card:NVIDIA GeForce 9600M GT up to 2302MB Total Available Graphics Memory with 512MB Dedicated
Graphic card type: Dedicated
Also I run all of my OSs on 64-bit Any more info I could provide please ask! >.>

---

### Post by P4man on 2009-08-12
ah, its a **laptop**. Lol. ok, then don't follow the monitor cable trying to find the videocard :)

Those temps look fine btw. Even surprisingly low. What happens when you stress the gpu?

---

### Post by Fox McCloud on 2009-08-12
Well, I just left the laptop sit in my seat while drove to pick up a trailer(I drive truck over the road) so a hour of sitting. The GPU reads 130F O.o and 125F CPU. It's sitting on my steering wheel getting cooled off.

It seems that the fans did not turn on, and it took almost 5-7mins to go back to normal. 104F GPU/ 93F CPU.

I guess the reason it even cools off is there is some fan movement, just no speed up.

How long is too long for the GPU to be so hot that it artifacts 3D images? I want to test it after each fix I try but I don't want to damage the GPU or CPU.

And...I just had a hard crash while editing this post. -_- That was the second time today, don't think it was related, because the temperatures where near normal.

---

### Post by P4man on 2009-08-13
those temperatures are not anywhere near dangerous or troublesome. I think we may have started this on the wrong foot so to speak, Temperatures over 70-80C° are not uncommon on laptops, and both cpu's and gpu's are typically spec'ed to run up to 100°C without failing, although you might have stability issues. You're not getting anything remotely close to that, and your laptop is still shutting down, so we better start looking elsewhere.

---

### Post by Onesimus on 2009-08-13
I don't know whether this link may help or not, but some of the symptoms are similiar.

[http://ubuntuforums.org/showthread.php?t=1186622]("http://ubuntuforums.org/showthread.php?t=1186622")

Could someone knowledgeable comment ?

---

### Post by Fox McCloud on 2009-08-14
Thanks for the replys. I've been a little busy.
> I don't know whether this link may help or not, but some of the symptoms are similiar.

[http://ubuntuforums.org/showthread.php?t=1186622](http://ubuntuforums.org/showthread.php?t=1186622)

Could someone knowledgeable comment ?I'll try what that user did in that thread.

---

