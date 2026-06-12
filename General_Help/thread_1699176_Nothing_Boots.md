---
title: "Nothing Boots"
date: 2011-03-03
forum: General Help
---

### Post by nosh276 on 2011-03-03
My harddrive crashed a few weeks ago and to hold me over, I've been using an Ubuntu Live USB, which has been great.

Unfortunately, now, it won't boot the live cd.

When I press the power button, I get the Toshiba splash screen, then it goes to a black screen with a solid white line in the top left corner (NOT flashing).

There is no text. I've let it hand for 7 minutes, it didn't change at all.

Am I totally screwed?

Any help is appreciated. I was going to buy a new harddrive this Saturday, now I don't know if I should.

Thanks in advance.:(:confused:

---

### Post by ameximes on 2011-03-03
There is something little confusing me. Are you using a USB Flash Disk or Live CD (Compact Disk) to Ubuntu?

Both, be sure your BIOS settings to boot your computer from what are you using (USB or CD).

I think you using a USB Flash Memory and someway your Flash Memory corrupted. 

Please try download an CD-ISO from => [here]("http://www.ubuntu.com/desktop/get-ubuntu/download")
if you don't have one and then burn it on a new empty CD then try to boot your system with this CD.

---

### Post by nosh276 on 2011-03-03
Sorry about that. I didn't realize I said both.

I'm using a Live USB.

I've tried two different flash drives on all 4 ports.


I'm using a netbook to make the Live USBs so I don't have a working CD drive--it's on the not-booting Toshiba.


:/

---

### Post by nosh276 on 2011-03-03
As a side note, I have been using Startup Disk Creator to make the USBs.

I'm now trying Unetbootin, hoping that may help.

---

### Post by nosh276 on 2011-03-03
Just tried with an Unetbootin made USB and it did the same thing. 

If I did somehow fry both of my flashdrives, I could pick up one tomorrow and also get a fresh download and try again.

It's been working for me for so long though.

Earlier today, when it last booted (it had not had any problems before the whole not starting at all problem), it said that I could install an additional driver for the graphics card (ATI something...). I didn't think, for some reason, that I'd have to restart.

Well I did, and that's when it wouldn't boot. I don't even get to a grub command line prompt or anything.

This is wholly frustrating.

---

### Post by JKyleOKC on 2011-03-03
The black screen with white line at top sounds like it's waiting for input. Since the problem appeared after you installed a new video driver, it's probably an incompatibility of that driver and your video hardware.

Try this when it gets to the black screen: press CTRL, ALT, and F2 all at the same time. If it's a video problem, you'll get a prompt for logging in that says it's on tty2. Log in as you usually do, but be aware that there won't be anything echoed to the screen when you enter your password. This will get you a terminal-style screen, and from there we can proceed to deal with the video problem.

Hope this helps!

---

### Post by nosh276 on 2011-03-03
> **JKyleOKC said:**
> The black screen with white line at top sounds like it's waiting for input. Since the problem appeared after you installed a new video driver, it's probably an incompatibility of that driver and your video hardware.

Try this when it gets to the black screen: press CTRL, ALT, and F2 all at the same time. If it's a video problem, you'll get a prompt for logging in that says it's on tty2. Log in as you usually do, but be aware that there won't be anything echoed to the screen when you enter your password. This will get you a terminal-style screen, and from there we can proceed to deal with the video problem.

Hope this helps!



It didn't do anything. It just stayed as the black screen with the white cursor line in the top left corner.

Would the driver matter if I'm using a fresh Live USB?


Also, using Unetbootin, I got a fresh download and made a new live USB, which still did not work.

---

### Post by JKyleOKC on 2011-03-03
In that case the problem may be something different; hopefully someone else will have more suggestions for you!

What happens if you press the left shift key while booting? If you get a menu of several choices, and more than the top two show as Linux versions, scroll down to the third line and hit Enter. This may get you back into operation and we can diagnose things in more detail.

If that also fails, try the same menu but choose one of the lines labeled "recovery" which will get you another menu that includes an option to fix broken video. That option may clear things up for you, or at least give more leads to help determine what is happening.

Using the Live CD/USB ought to avoid any problems not due to hardware failure, however. Can you get to your BIOS setup screens (usually there's an initial splash screen when you power up, that tells you which key to press to get to the setup screens)? If you can, search for any settings dealing with the video display and let us know what you find. I remember one recent thread that was resolved by changing a BIOS setting that had somehow been turned off...

---

### Post by ameximes on 2011-03-03
Simply let's get ensure what is working well before what is wrong about your system.

1. Try your USB Stick with another computer (your netbook?)
A. If it's working well then we will focus on your Toshiba.
B. If not then you know what we have to do, create a new USB drive to (go to step 1) test with another computer. 

Focusing on Toshiba: 
When we have a working USB there is three probability that I doubt about.

1. Driver issue
> 
install an additional driver for the graphics card (ATI something...)


I don't know if Ubuntu store your "driver" files on your internal harddisk but I think it's doing this. Otherwise this information and files (about driver) must stored on your USB (But according to your declaration storing things on USB can't be the cause your problem because you already refreshed this). If the driver stored into internal hard-disk and someway the drivers problematic you have to repair or remove or disable this driver in order to use your computer.

I never use a live distro in long-term and I can't be sure but if my memory not mislead me when you boot your computer with any live distros it is ask you to what you want to do (GRUB or LILO Screen).

In this screen Ubuntu provide you a recovery mode (without X, minimum drivers and a Console), try to log in to this and look for a directory or a file that created by Ubuntu.

Anyway if we in this situation consider about details further.

2. BIOS Level problems.
If you just see a splash and then a cursor that blinking top of the screen and CTRL+ALT+F(1-6) not respond then I say, your computer can't read and/or process OS from USB.
Try to boot computer without any USB or CD and tell us what you see. A blinking cursor or a message like "no disk found press any key..."

If you still see a cursor your problem is not about Ubuntu.

I insist to you to check your BIOS setting and boot sequence again.

3. An hardware problem
Remove your harddisk physically or disable it from BIOS then try again both boot with and without USB and check the results.


An alternate, try to boot your computer with any other live distro like minix or memphis and check the results.

---

### Post by nosh276 on 2011-03-03
Pressing or holding Left Shift during boot doesn't do anything.

I can get into the BIOS settings--and have pictures of settings below.

I tried booting without USB and it goes to the same cursor (NOT BLINKING).

Pressing CTRL + ALT + F(1-6) on the cursor screen doesn't have any effect.

I'll try without the harddrive in now and post back in a minute.


BIOS Settings:

[ATTACH]184994[/ATTACH][ATTACH]184995[/ATTACH][ATTACH]184996[/ATTACH][ATTACH]184997[/ATTACH]

---

### Post by nosh276 on 2011-03-03
I took out the drive and tried to boot and it finally did something different :)
[ATTACH]184998[/ATTACH]

This is what it showed when my harddrive first crashed.

I then tried booting with the USB and it WORKED.

I don't know why the failed harddrive would mess up booting from USB, when USB is first in the boot order and I even tried it by selecting USB manually in the boot options.


I ran a disk check using the live usb before booting into Ubuntu. 

After the disk check, I hit OK to reboot, and it worked straight away.


So, here's my question: Since I am now able to boot to the USB, I should have no problems once I install a new harddrive, right

---

### Post by JKyleOKC on 2011-03-03
> **nosh276 said:**
> I don't know why the failed harddrive would mess up booting from USB, when USB is first in the boot order and I even tried it by selecting USB manually in the boot options.I've been told that Ubuntu will use the "swap" partition on the hard drive even when booting from the Live CD, if one exists. That could well be why it was keeping you from booting from the USB. At any rate it's good that you've been able to get things going again.

I would expect installing a new hard drive should take care of everything. Get the largest you can afford, and I suggest that you create four partitions: one primary of 40-50 GiB for /, an extended taking the rest of the drive, and within the extended, one swap that's twice as large as your RAM (rounded up to the next GiB), and the rest of the extended as /home. This will let you do version upgrades without losing your data, since all of it will be in the /home partition and the system itself will be on /.

---

### Post by nosh276 on 2011-03-03
> **JKyleOKC said:**
> I've been told that Ubuntu will use the "swap" partition on the hard drive even when booting from the Live CD, if one exists. That could well be why it was keeping you from booting from the USB. At any rate it's good that you've been able to get things going again.

I would expect installing a new hard drive should take care of everything. Get the largest you can afford, and I suggest that you create four partitions: one primary of 40-50 GiB for /, an extended taking the rest of the drive, and within the extended, one swap that's twice as large as your RAM (rounded up to the next GiB), and the rest of the extended as /home. This will let you do version upgrades without losing your data, since all of it will be in the /home partition and the system itself will be on /.


Thanks for all of the help.

I'm excited about my new harddrive.

---

### Post by ameximes on 2011-03-04
Left Shift is Windows's hot key to see additional boot options.

What about trying USB stick on another computer?
In BIOS visuals (1) ti seems there is no hard-disk connected your system is that true?

---

