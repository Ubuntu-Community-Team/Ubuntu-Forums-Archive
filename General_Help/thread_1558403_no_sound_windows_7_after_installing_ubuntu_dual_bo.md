---
title: "no sound windows 7 after installing ubuntu dual boot"
date: 2010-08-22
forum: General Help
---

### Post by manjiboy on 2010-08-22
I have an Asus Xonar DS, and am getting no sound in Windows whatsoever. I'm pretty sure something in Ubuntu is causing the problem as this only started happening after I installed it. I used to get heavily distorted sound in Windows, and now nothing at all. I've tried removing pulseaudio and disabled alsa, restarted ubuntu and then went into Windows, and it didn't help. Sound is 100% fine in ubuntu. Any help appreciated, thanks.

---

### Post by manjiboy on 2010-08-22
nobody have any ideas? I'm pretty sure this isn't a W7 problem as I've reinstalled the drivers and checked settings etc. to death, everything is set up OK...

---

### Post by sdemsc on 2010-08-22
can you tell whether sound is playing in ubuntu.becoz i think that you might have a hardware issue

---

### Post by sdemsc on 2010-08-22
oh i am sorry you have already mentioned that sound is fine in ubuntu.

---

### Post by manjiboy on 2010-08-22
Yea just Windows, very annoying. I'm thinking about just reformatting and sticking with just windows. Thanks for the reply :)

---

### Post by dougalkerr on 2010-08-22
There is no way that Ubuntu will have affected your Windows sound card drivers. It sounds like it was something waiting to happen and by coincidence...

I use Windows 7 and Ultimate Edition at work and Windows 7 does have the odd thing happening with drivers. I share an HP Deskjet with a colleague and Ultimate Edition Linux finds and uses the printer without fault.
Windows 7 says it downloads the latest driver for the printer and even though I delete and reinstall the driver manually Windows 7 insists that there is nothing wrong with the driver but, it cannot find the printer to print to...

Typical Microsoft.

Can you try another sound card at all with Windows to see if your sound card driver for Windows is the problem?

---

### Post by doktarZues on 2010-08-22
> **dougalkerr said:**
> There is no way that Ubuntu will have affected your Windows sound card drivers. It sounds like it was something waiting to happen and by coincidence...

I agree--definitely sounds like a coincidence.  Unfortunately I don't have anything helpful to add but I can't come up with a reasonably possible scenario where Ubuntu being loaded could cause a Windows sound conflict.  I suppose that the activity to the hd that Ubuntu did at installation* could* have caused an issue with the device/driver files Windows uses but like you said, reinstalling the drivers should correct that.  

Fortunately I'm having a better go with Ubuntu and Windows hasn't been booted outside of the occasional VM for several months now. Good luck, hope you get it all sorted out.

---

### Post by manjiboy on 2010-08-22
Some other people have had the same problem:
[http://ubuntuforums.org/showthread.php?t=1519109](http://ubuntuforums.org/showthread.php?t=1519109)

One reason I think it could be related to Ubuntu is cos of a loud clicking the soundcard makes. It makes that noise whenever you install drivers for it, or when I try to enable/disable it in Windows, and it also does that whenever I shut down Ubuntu. There could be some kind of switch on the card that Ubuntu is setting that prevents it from working in W7.

I have recently re-downloaded and installed the drivers in win7, and they were updated pretty recently (1st aug) but I've had the problem with the older win drivers that I've had working for a long time now. I don't think windows auto updates them so it's unlikely to be dodgy drivers.

edit: oh and no I dont have another sound card unfortunately

---

### Post by dougalkerr on 2010-08-22
Doubt very much that Ubuntu is setting any kind of switch, that would mean an chip or such on the sound card that accepts such a thing. I don't think it could set any kind of permanent switch on the sound card that Windows wouldn't then just reset.

You should contact the sound card manufacturer or check out their site for any such problems.

Still think it is pure coincidence that all your problems started with the Ubuntu install.

Do you NEED Windows?

An option would be to install VirtualBox in Ubuntu and then install Windows as a guest system but, it would take a little time and perseverance to get things done and of course you would have to install all your Windows programs again.

Typical eh? just when you thought things were going well...

Sorry we haven't been able to help a bit better.
Just a thought... I remember that some motherboards used to have inbuilt sound chips and then the PC manufacturer would add another card onto the motherboard and it would have additional features, etc over the simple sound chip on the motherboard.
It is possible that the BIOS settings are set to use the motherboard (onboard) sound chip and Windows would usually override this with the other sound card driver settings.

You could have a look at the BIOS settings (F2 or Del or something when the PC boot screen starts). Opt to switch off the onboard chip if you know you have an additional card - you can easily switch it back on at next boot.

---

### Post by manjiboy on 2010-08-22
Yea I'm gonna try the manufacturer's forum for help. And I really want windows to play games in. I know you can play many in ubuntu with wine but they are really hard to get to work lol :) (fallout 3 just doesnt run at all grr)

How well does Win7 run in a virtualbox compared to normal? I'd expect it be pretty slow, not good for gaming. Thanks anyway for trying to help guys, I'll give the BIOS thing a look.

---

### Post by HeadHunter00 on 2010-08-22
Pretty odd problem. Although that shouldn't happen cuz ubuntu doesn't interfere with the windows installation. Just creates another filesystem and installs GRUB.

---

### Post by doktarZues on 2010-08-22
> **manjiboy said:**
> How well does Win7 run in a virtualbox compared to normal? I'd expect it be pretty slow, not good for gaming. Thanks anyway for trying to help guys, I'll give the BIOS thing a look.

Wine or dual-booting is your only option for games. VM and virtualbox can't even come close to the output games require.  Everything (other than games) that I've put into virtualbox has ran really well.

---

### Post by HeadHunter00 on 2010-08-22
> **doktarZues said:**
> Wine or dual-booting is your only option for games. VM and virtualbox can't even come close to the output games require.  Everything (other than games) that I've put into virtualbox has ran really well.
Exactly.

---

### Post by dougalkerr on 2010-08-22
Yep it is true. things run slower in VirtualBox even though it is getting better all the time and you can allocate a RAM as much as you like to the limit of both Host and guest systems (so really you need even more RAM than usual if you want to do anything graphic intensive).

So, good luck with the manufacturer or the BIOS checking.

---

### Post by wellington7 on 2011-12-18
I know this is an old post. But, today, I'm having this same problem. A colleague explained me that by re-sizing the HD with Windows already installed may cause that.

I don't really know the explanation, but the solution is to partitionate the HD first, and them install Windows and Ubuntu.

Very annoying, because I'll have to find the serial key of the Windows that came with my PC and do all this work of reinstalling.. :(

---

### Post by Mark Phelps on 2011-12-18
> **wellington7 said:**
> I know this is an old post. But, today, I'm having this same problem. A colleague explained me that by re-sizing the HD with Windows already installed may cause that.

I don't really know the explanation, but the solution is to partitionate the HD first, and them install Windows and Ubuntu.

Very annoying, because I'll have to find the serial key of the Windows that came with my PC and do all this work of reinstalling.. :(

Actually ... NO ... you won't.

Your fried is right in that allowing the Ubuntu installer to resize Win7 OSs can result in problems back in Win7.  

But, you don't have to reinstall to get around this.

You just have to use the RIGHT tool to resize the Win7 OS partition -- the Win7 Disk Management tool. After you do the resize, reboot into Win7 a couple of times to allow the filesystem to make adjustments.

Then, use manual partitioning in the Ubuntu installer to install Ubuntu.

No need to reinstall Win7 to install Ubuntu second in a dual-boot setup.

---

