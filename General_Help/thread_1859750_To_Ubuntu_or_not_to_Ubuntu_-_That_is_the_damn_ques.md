---
title: "To Ubuntu or not to Ubuntu - That is the damn question"
date: 2011-10-14
forum: General Help
---

### Post by tman69 on 2011-10-14
Morning and thanks in advance for any and all help!!!
 
I have read many postings on the blinking cursor issue but none seem to have any solutions which work and most are issues after install but I am not getting that far. I have read some postings about it possibly being Nvidia related but I am not getting through the install so not sure that applies. Here is the situation and I am hoping someone out there can help.
 
I am an intermediate Linux user but have installed various flavors including both 32 and 64bit and both client/server versions with no issues on other machines. 
 
I am building an HTPC and decided I would like to use Ubuntu. I have tried 11.04 and 10.04 both 32 and 64 bit with the same results. 
 
BIOS posts 
boot from CD
Ubuntu screen comes up to choose language
Select install Ubuntu
screen flashes a few quick times
BLINKING CURSOR
no CD drive or HDD activity apparent
 
That's it. I have tried pressing F6 and marking all of the items in there (except for the free software only). I have also tried taking off the "quiet splash" and replacing it with "xforcevesa". When I do that I get text and it looks like it is installing but then it stops. I have only did this one time so I do not know if it stops at the same exact text each time and I am currently at work so I can't provide the text where it stopped at this moment.
 
Here is the hardware setup (all brand new, except video card which was from another machine of mine):
 
Biostar A770E3 MB
 
AMD Athlon II X2 250 Regor dual-core 3Ghz 
 
G. Skill (2 x 4GB) DDR3 1333
 
620Watt 80 Plus Certified PS
 
EVGA 8800GTS 512MB
 
ASUS My Cinema PE9400 Combo (Tuner Card)
 
 
Again, many thanks to any and all help you can offer as I really don't want to go with Windows on this box unless I absolutely have to do so.

---

### Post by WasMeHere on 2011-10-14
Hi tman69,

You have done more than should be expected to get Ubuntu running IMHO.
Let us hope a real expert on boot issues will show up and help you!

Good luck
Olle

---

### Post by IWantFroyo on 2011-10-14
I would recommend using 11.10. 11.04 is known to have issues, and 10.04 doesn't have up to date hardware support.

---

### Post by CatKiller on 2011-10-14
Graphics issues can definitely be a pain. There is a text-based installer on the alternate cd that might help you get Ubuntu installed so that you can see logs to establish where the problem lies.

---

### Post by WorMzy on 2011-10-14
I'm not familiar with the xforcevesa option, but have you tried booting with nomodeset?

---

### Post by coldraven on 2011-10-14
Does it make a difference if the box is cable connected to the internet when you try and install?

---

### Post by tman69 on 2011-10-14
Thanks for all the responses!
 
I will try using the 11.10 version tonight.
 
How do you do the text based installer?
 
I have tried the nomodeset option under F6, in fact as mentioned I tried all of those options.
 
I did not have it connected to the internet at all, but I could easily have it connected via hard wire if you think it would make any difference.

---

### Post by CatKiller on 2011-10-14
The alternate cd is just another iso from the same place you got your standard Ubuntu image from. It works the same way as the normal install, it just doesn't try to boot to a desktop first. I believe it also lets you set it up in different ways; minimal and some others that I can't recall at the moment. You can still do a standard ubuntu-desktop install, though.

---

### Post by tman69 on 2011-10-14
Found it. Didn't see the alternate link. I will try this version when I get home per your suggestion. Thanks.

---

### Post by tman69 on 2011-10-14
Still no love from Ubuntu.

I made a new CD using the alternate 11.10 amd64 ISO. I even took out one stick of ram and swapped out my 8800GTS for another older video card though it is still an Nvidia card. With the alternate version I went in to F6 and selected all the options except Expert Mode and the Free Software choice.

I also tried it the way it is by default by just selecting install and I did all the options plus replaced quiet with xforcevesa. What I get is it screen flickers a couple times then goes to a black screen. No blinking cursor...and there is no activity showing from the CD rom drive. Just sits at a black screen.

Oh and per suggestion I connected an ethernet cable as well.

---

### Post by CatKiller on 2011-10-14
Random shot in the dark before I think of something else: either install disc will have the option of running a check on the integrity of the files. A bad burn has unpredictable effects.

---

### Post by tman69 on 2011-10-14
I appreciate the thought regarding a bad burn but I have tried 3 different versions on 3 different disks and tried bootable USB also.

Currently I found where someone said to do F6 and nomodeset then change "quiet" with "i915.modeset=0 xforcevesa" and I also selected all the other options in F6 like I have done before. This brings up a bunch of text like it is installing but then it stops. It stopped at a message about "[0.036335] Switch to broadcast mode on CPU0". And that is where it sits right now.

---

### Post by coldraven on 2011-10-15
I can only suggest that you try cleaning the CD lens. I had three brand new DVDs and it took three cleans of the lens before all three would play. In my case the lens looked clean but possibly had a film of nicotine *cough* on it. I used a cotton bud and methylated spirit.

Ooops! just read the USB boot part. Too much whisky last night :)

---

### Post by tman69 on 2011-10-16
Still no go....

I have tried 2 different video cards, 3 different optical drives, several different IDE hard drives, and am right now trying a SATA drive. I have tried 11.04, 11.10, 10.04...including various 32 or 64 bit and also the alternate version.

I have tried various options as previously stated.

I am running out of ideas.

I thought perhaps it is possibly installing while there is only the blinking cursor but I have left it sit and no change.

Any other ideas? I did install Windows XP Pro 64 bit on the same machine yesterday using the same optical and IDE hard drive I have been trying to use with Ubuntu.

Does anyone have any other distribution suggestion perhaps besides Ubuntu keeping in mind the purpose of this machine is to be an HTPC with a tuner card running XBMC with perhaps MythTV for Live TV watching/recording. 

Thanks for any and all help!

---

### Post by CatKiller on 2011-10-16
I've found similar posts where the culprit seemed to be problems with the USB controller. Might be another line of attack.

---

### Post by tman69 on 2011-10-16
Another line of attack how?
 
I found postings about it being because of DVI and if you use a DVI to VGA adapter it works...tried it but doesn't work for me.
 
I can hold shift before getting to the language selection choice and get it to a prompt of:
 
Boot:
 
However, I am not certain what arguments I need to add after install-live to make it work with my Nvidia 8800GTS, which I still think may be causing the issue.

---

### Post by crjackson on 2011-10-16
tman, I almost went back to 10.10 due to issues with my nVidia 8800GTS card.  Look at this thread (mine) and see if anything useful pops out at you...

[http://ubuntuforums.org/showthread.php?t=1857588]("http://ubuntuforums.org/showthread.php?t=1857588")

---

### Post by CatKiller on 2011-10-17
> **tman69 said:**
> Another line of attack how?


By changing USB settings in the BIOS, some people reported success.

If the text-based install didn't work, I don't think it's a graphics issue although I must admit I haven't used the text installer for a while so it's possible that it still does some graphics stuff.

---

### Post by tman69 on 2011-10-17
Hey CRJACKSON, I reviewed your thread and I see EFFENBERG0x0 had some very detailed advice. The only thing is you had an install whereas I don't. I get the choose your language and then when I hit enter on the install option I get a blinking cursor so it never installs. I did see the mention of clicking the F6 option about Free Software and I have not ever tried clicking that option so when I get home from work today I am going to give that a try. And when/if that fails I am going to try installing Ubuntu 7...as thus far no version of Ubuntu, Kubuntu, or LinuxMCE has installed for me on this machine.
 
CatKiller, what USB settings in BIOS? What do they change? I'll try anything at this point. Also, I wouldn't say it was a text-install failure as I may have done something incorrect in the arguments I used.
 
I've never known it to be this hard to install Linux before but it is almost to the point where I have to give up and run Windows. I've had the computer built since last Thursday or Friday and no matter how many versions I try I get the same results...but I haven't given up yet just need more suggestions.
 
Thanks!

---

### Post by goldshirt9 on 2011-10-17
can you actually run a live cd.
i have on occasions found that i cannot install straight from the cd , i have to run the live cd option and install that way .
no idea why and i am far from being a expert in these matters but maybe my experience may help .:confused:
dont give up. :):):):)

---

### Post by effenberg0x0 on 2011-10-17
tman69, I'm not familiar with such a situation although once in a while I do see some reports. I will try to help, but it may take a while for us to find the cause. Being an unusual bug, I'm interested in knowing why it happens.

First things I'd like to know: 

1) When you boot your PC and go into the BIOS (generally by holding del ou F2 - depends on the brand). do you see options for AHCI/IDE mode for the HDDs? Does it have a EHCI / EHCI Hand-Off setting? What about USB Speed / USB Legacy SUpport?

2) Is this a laptop or a desktop? If its a laptop from a known brand, tell me the  brand/model.

3) Do you know it it uses EFI/UEFI (generally MACs use it)

4) Have you tried installing from a Live USB instead of a Live CD?

5) Is windows or other Operating System installed in this PC as well?

6) Still in the BIOS. Mostly every BIOS allow you to change, enable, disable devices that should be looked at at boot time. Normally it is set to try the USB, then the CD, then the first HD. Try to setup this way. Remove any external storage device you might have connected to the PC: memory card, SDCard, USB HDD, USB Stick, Smart Phone, iPod, Printer with Flash memory, etc. We have to eliminate variables.

7) How much RAM do you have?

8) Is this machine overclocked?

Effenberg

---

### Post by tman69 on 2011-10-17
> **effenberg0x0 said:**
> tman69, I'm not familiar with such a situation although once in a while I do see some reports. I will try to help, but it may take a while for us to find the cause. Being an unusual bug, I'm interested in knowing why it happens.
 
First things I'd like to know: 
 
1) When you boot your PC and go into the BIOS (generally by holding del ou F2 - depends on the brand). do you see options for AHCI/IDE mode for the HDDs? Does it have a EHCI / EHCI Hand-Off setting? What about USB Speed / USB Legacy SUpport?
 
2) Is this a laptop or a desktop? If its a laptop from a known brand, tell me the brand/model.
 
3) Do you know it it uses EFI/UEFI (generally MACs use it)
 
4) Have you tried installing from a Live USB instead of a Live CD?
 
5) Is windows or other Operating System installed in this PC as well?
 
6) Still in the BIOS. Mostly every BIOS allow you to change, enable, disable devices that should be looked at at boot time. Normally it is set to try the USB, then the CD, then the first HD. Try to setup this way. Remove any external storage device you might have connected to the PC: memory card, SDCard, USB HDD, USB Stick, Smart Phone, iPod, Printer with Flash memory, etc. We have to eliminate variables.
 
7) How much RAM do you have?
 
8) Is this machine overclocked?
 
Effenberg
 
I am currently at work so I will have to check the BIOS options you asked about when I get home. It is a Biostar board with American Megatrends BIOS.
 
This is a desktop not a laptop using all brand new components from NewEgg except the Nvidia graphics card.
 
Yes, I tried the USB boot and it brings up the menu but I could not select any options. It acted like it froze on the menu and the keyboard didn't respond to any input.
 
There is no other OS installed. I have tried several different drives and currently have a 500GB Sata drive attached.
 
There are no other drives connected. One SATA hard drive and one IDE optical drive. The BIOS is set to boot CD then HD. In order to do USB, you have to connect the USB go in to BIOS setup, set the USB emulation, save changes, go back in to BIOS setup again and set that device in the Boot Priority.
 
I have 2 x 4GB sticks of RAM (I did try installing with only one stick also) and no it is not overclocked.
 
For more system specifics see my original post for processor/motherboard details if you need them.
 
Thanks!!!

---

### Post by effenberg0x0 on 2011-10-17
It would be important for you to try two parameters in the install disk. Before you boot, make sure you go to the BIOS and use the option "Load Defaults", save and exit.

See the procedures at [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) and the topic 
"Changing the CD Boot Option Configuration Line" for instructions on how to apply these parameters. try one at a time. Don't mix them. Remove quiet, splash, nomodeset, acpi=off, acpi=force and any other parameter you see in the boot options configuration line.

Disconnect all possible USB peripherals from the PC before trying. 
 [B]
[COLOR=Red]EDIT[/COLOR]:[COLOR=Red] Added debug parameter[/COLOR][/B]
1) acpi_osi="Windows 2006" mem=1024M irqpoll drm.debug=0x4 
2) acpi_osi= mem=1024M irqpoll drm.debug=0x4 

When you get to the blinking console, try capslock, numlock, see if lights turn on/off in the keyboard. DIsconnect / connect a USB device, see if there's any change  message displayed. Wait about 10 minutes before giving up. Try to Ctrl+Alt+F1 to F6 during the process, including at minute 10, before giving up. If you manage to see console messages, take note of the last, or the ones marked as errors/warnings. We need to see some sort of error message in order to really nail this one.

Q) Have you ever upgraded your BIOS? Check manufacturer website for downloads / Bios Updates and compare to your version. There might be a bug and a fix for it.

Regards,
Effenberg

---

### Post by tman69 on 2011-10-17
Here is a link to a video I made of me trying to install LinuxMCE 64bit DVD. I basically get the same results using all the distros and 32/64 bit disks.

[http://www.youtube.com/watch?v=dNN5Ame0nTc](http://www.youtube.com/watch?v=dNN5Ame0nTc)

As for your other suggestions I will review and try what I can after I get back from picking up my son in about 40 minutes.

Thanks.

---

### Post by effenberg0x0 on 2011-10-17
I've seen the video. It looks like its trying to enter a gfx mode (see the message about it flash right after the blinking cursor shows). On a normal setup, the cursor would blink 1 or 2 seconds and enter a graphic mode.

Your EVGA card has two DVI ports. Make sure DVI cable is connected to port #1. Are you using a DVI-VGA adapter to connect to LCD? 

I think you should try using the Oneiric normal install ISO. You'll be presented with the option to start Ubuntu from CD and later install it. It will have the opportunity to make all changes to your system before reboot. 

But please also try the options mentioned earlier. You can try with this CD you used in the video. When you get to the part where you select acpi, free software, etc., you have the option of directly editing the kernel line. I see you still have quiet and splash there. These options are bad in your case, and they should be removed. All they do is try to load a logo in screen, that wouldn't allow us to view error messages. For all I know, the blinking cursor can very well be the system trying to load this image and failing.

Regards,
Effenberg

---

### Post by tman69 on 2011-10-17
> **effenberg0x0 said:**
> I've seen the video. It looks like its trying to enter a gfx mode (see the message about it flash right after the blinking cursor shows). On a normal setup, the cursor would blink 1 or 2 seconds and enter a graphic mode.

Your EVGA card has two DVI ports. Make sure DVI cable is connected to port #1. Are you using a DVI-VGA adapter to connect to LCD? 

I think you should try using the Oneiric normal install ISO. You'll be presented with the option to start Ubuntu from CD and later install it. It will have the opportunity to make all changes to your system before reboot. 

But please also try the options mentioned earlier. You can try with this CD you used in the video. When you get to the part where you select acpi, free software, etc., you have the option of directly editing the kernel line. I see you still have quiet and splash there. These options are bad in your case, and they should be removed. All they do is try to load a logo in screen, that wouldn't allow us to view error messages. For all I know, the blinking cursor can very well be the system trying to load this image and failing.

Regards,
Effenberg

I am using a DVI-VGA adapter as I read some postings that this was needed. I'm not certain which port is port 1.

Could you tell me exactly what you think I should enter at the kernel line? I'm not sure which options to use or not use.

---

### Post by tman69 on 2011-10-17
> **tman69 said:**
> I am using a DVI-VGA adapter as I read some postings that this was needed. I'm not certain which port is port 1.

Could you tell me exactly what you think I should enter at the kernel line? I'm not sure which options to use or not use.

I also tried using Ubuntu 7.1 64bit, tried switching to other DVI port and with that version you can use F4 to set the resolution which I set to 1024x768 and I removed the "quiet splash" from the boot line and instead of a blinking cursor I get a black screen. Also when it went to the next screen the black screen, I did not see any screen flash and the keyboard no longer responds.

---

### Post by effenberg0x0 on 2011-10-17
This is not an Apple keyboard, is it?

---

### Post by effenberg0x0 on 2011-10-17
> **tman69 said:**
> I am using a DVI-VGA adapter as I read some postings that this was needed. I'm not certain which port is port 1.

Could you tell me exactly what you think I should enter at the kernel line? I'm not sure which options to use or not use.

There's a theory that one shouldn't use a DVI-VGA adapter but preferably a monitor with DVI port. I'm not sure where I stand on it.

Look here: **[https://help.ubuntu.com/community/BootOptions#F6.%20Other]("https://help.ubuntu.com/community/BootOptions#F6.%20Other")**
Search the page for "**Changing the CD Boot Option Configuration Line**"
There's a screenshot right above.

In this screenshot, where you see **quiet splash -- vga=791** you should remove it and enter this:

**First Test:**
acpi_osi="Windows 2006"  mem=1024M  irqpoll  drm.debug=0x4

**Second test:**
acpi_osi=  mem=1024M  irqpoll  drm.debug=0x4

**[COLOR=Red]EDIT[/COLOR]**
Check out this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/855449](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/855449)
Looks identical to what you see there.

---

### Post by tman69 on 2011-10-17
> **effenberg0x0 said:**
> There's a theory that one shouldn't use a DVI-VGA adapter but preferably a monitor with DVI port. I'm not sure where I stand on it.

Look here: **[https://help.ubuntu.com/community/BootOptions#F6.%20Other]("https://help.ubuntu.com/community/BootOptions#F6.%20Other")**
Search the page for "**Changing the CD Boot Option Configuration Line**"
There's a screenshot right above.

In this screenshot, where you see **quiet splash -- vga=791** you should remove it and enter this:

**First Test:**
acpi_osi="Windows 2006"  mem=1024M  irqpoll  drm.debug=0x4

**Second test:**
acpi_osi=  mem=1024M  irqpoll  drm.debug=0x4

**[COLOR=Red]EDIT[/COLOR]**
Check out this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/855449](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/855449)
Looks identical to what you see there.

Okay, I replaced the "quiet splash" with your first test and it stopped on:
2.574654 Freeing initrd memory: 14220k freed

I left it here for about 15 minutes. Then I tried your second test with much the same result. It stopped at:
2.589902 Freeing initrd memory: 14220k freed


Oh, and no I am not using an apple keyboard! :)

---

### Post by effenberg0x0 on 2011-10-17
```
2.574654 Freeing initrd memory: 14220k freed
```One message :) well, its something. At this point did you attempt to switch to a VT or it stopped on the same blinking cursor?

Try this one now:
```

acpi=oldboot nolapic noapic mem=1024M  irqpoll  drm.debug=0x4
```

---

### Post by tman69 on 2011-10-17
> **effenberg0x0 said:**
> ```
2.574654 Freeing initrd memory: 14220k freed
```One message :) well, its something. At this point did you attempt to switch to a VT or it stopped on the same blinking cursor?

Try this one now:
```

acpi=oldboot nolapic noapic mem=1024M  irqpoll  drm.debug=0x4
```

There were several other lines of text before it stopped at the freeing memory message. It just stayed on that screen and I left it alone thinking perhaps it was doing something.

I also have some other information you asked for previously concerning BIOS.

Legacy USB Support is enabled

USB 2.0 Controller Mode is HiSpeed

BIOS EHCI HandOff is enabled

Currently I have it running the mem test from the Live CD

I will try your new line of boot options and be back in a minute.

---

### Post by effenberg0x0 on 2011-10-17
I edited the second test a little:
```
acpi=off nolapic noapic mem=1024M  nousb irqpoll  drm.debug=0x4 bootmem_debug debug debugpat dynamic_printk earlyprintk=vga initcall_debug
loglevel=7 mminit_loglevel=4 pnp.debug sched_debug 
```I think I know where its stuck at. If you try this line and still have no success, go to your BIOS, change USB speed to normal, not hispeed, deactivate EHCI handoff and try again.

---

### Post by tman69 on 2011-10-17
> **effenberg0x0 said:**
> I edited the second test a little:
```
acpi=off nolapic noapic mem=1024M  nousb irqpoll  drm.debug=0x4 bootmem_debug debug debugpat dynamic_printk earlyprintk=vga initcall_debug
loglevel=7 mminit_loglevel=4 pnp.debug sched_debug 
```I think I know where its stuck at. If you try this line and still have no success, go to your BIOS, change USB speed to normal, not hispeed, deactivate EHCI handoff and try again.

Well....I don't think I will get the chance to try your edited version....since it is installing right now!!!! 

Your last posting of:

acpi=oldboot nolapic noapic mem=1024M irqpoll drm.debug=0x4

WORKED! So far...<fingers crossed>

Though it was odd....I exited the memory test and it does a fast reboot, used your command and the thing started going nuts...text was a flying by...next thing you know I am at a desktop getting ready to install. However, I wasn't sure which disk I had in there so I exited. Looked at which disk and it was the right one. So I turned it back on and did your command again and nothing.

I was pissed at myself for exiting and was like what the hell it just worked. I tried it twice more and it froze like it had previously. I hadn't did anything different except the mem test...that couldn't be it...but I have tried everything else so why not...I started the mem test, exited it, used your command, and BINGO back to an install desktop. So it is installing right now.

Could not have done it without your help. I will post back in a little bit once I know if the install is actually successful and I can reboot a few times and still get in to the system.

Thank you all!

---

### Post by effenberg0x0 on 2011-10-17
Very cool :) the difference from the first to the second version was just to gather a little more debug info as you can see. I'm gonna put my money on the nolapic option.

Look, you have to be aware of one thing: As the setup asks you to reboot, you might get stuck out again. Why? Because Grub command line won't have those options. 

We need to put them as defaults for grub, so they are always there. As soon as you have the opportunity, you have to edit /etc/default/grub (sudo nano /etc/default/grub) and add those options to the section
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```so that it will look like
```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=oldboot nolapic noapic mem=1024M irqpoll drm.debug=0x4"
```and run the command 
```
sudo update-grub
```That way, they will always be there, even if you upgrade, etc.

By the way, if you're not installing Oneiric, you should, now that you know what you have to put on Grub as kernel options.

Let me know how the install went. 

Effenberg


PS: Later, when you have the system working, you can try editing that line. I am pretty sure you can remove mem=1024M irqpoll drm.debug=0x4 which was just to get debug info.

---

### Post by tman69 on 2011-10-17
The version I installed is 11.10 64bit. It worked on reboot without making any changes. I am currently updating the Nvidia drivers to the recommended current version with updates.

But I will keep this information in mind if I have issues later.

Again, THANK YOU!!!!

---

### Post by effenberg0x0 on 2011-10-17
Very nice, have fun man.

Effenberg

---

