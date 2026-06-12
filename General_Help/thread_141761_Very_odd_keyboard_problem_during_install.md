---
title: "Very odd keyboard problem during install"
date: 2006-03-09
forum: General Help
---

### Post by Podo on 2006-03-09
Hey, thanks for taking the time to read this. I have a very odd problem with linux that doesn't seem to be limited to Ubuntu, but is not a problem with all distros of linux. I figured I'd post here since Ubuntu is what I want to run the most.

What happens is that after hitting enter to start the install and the drivers are loading my keyboard and mouse no longer recieve any power. This happen right in the middle of loading the USB drivers. It continues to load and go to the language select screen, but of course I cannot select a language with my keyboard not functioning. I have tried many possible workarounds. I have tries a server install, i have tried telling Ubuntu to not probe USB devices, i have tried tricking it by unplugging the keyboard before the drivers load, and I have tried using a PS2 keyboard and mouse. The PS2 keyboard and mouse retain the power from the PC (the lights stay on), but the SECOND i hit enter the keyboard no longer functions. I can hit num lock all day and the light will not turn off. I have looked into my bios and USB is enabled. Somebody else mentioned try allowing legacy HID to maybe fix the PS2 problem in my bios but I didn't find that option anywhere.

As I said this is not Ubuntu specific (both 32 and 64 bit). I have had this problem on mepis as well. I tried installing Fedora core 1 that come with a school book of mine and that went fine. That led me to believe it was a problem with Debian based linux so i tried Mandriva. Same exact issue there as well. I'm really at a loss of what the problem may be. Perhaps newer Linux kernals don't support my motherboard? That doesn't really make much sence to me though. I have been searching for a couple days on the problem and have only came across a couple of threads that were my problem and neither had any responses. I have installed ubuntu on vmware (but had a driver issue with the video driver from VMware, so no GUI but it worked) and on an old compaq 233mhz (no gui there either, not enough ram... i yanked the hard drive and stuck it in this machine because I want to switch to Linux as my main OS).

Any ideas? I really don't want to continue using fedora, I've gotten somewhat sick of it from using it in school, hehe.

---

### Post by patsissons on 2006-03-09
Is this an older computer or is it somewhat recent?  I know I had ridiculous troubles installing linux on one of my older machines, it was almost random if the install would work or not.  I had video errors, memory errors, hard drive errors, you name it.  As it turned out in the end, what needed to be done was I had to set the hard drive to LBA mode for the first part of the install, then back to normal after the reset.  Seemed to fix all the problems.  I guess what I'm getting at is that if your machine is older, you may have to fiddle around with the bios.  If it is a newer machine, then I'm pretty stumped, maybe see if a live disc will load up properly?

---

### Post by Podo on 2006-03-09
Is is a new machine. AMD 64 3200+, 1 gig of ram, x800xl video card, onboard gigabit nic and 7.1 sound. The motherboard is a Chaintech nForce 4. The hard drive I'm loading it on is only a 20gig ide drive, not sure if it's 5400 or 7200. My windows is on a raid 0 of 2 sata 7200rpm 80 gig drives. I'm thinking that maybe i should try fedora core 4 and see if that works, if it doesn't then it's probably a problem with the newer linux kernals and maybe I should try older versions of other distros. I'd rather be up to date though, hehe.

---

### Post by Podo on 2006-03-10
I've now tried vector and xandros with the same problem. Damn Small has the same problem, but since there's no interaction until it is fully loaded the os loads fine. Freesbie loads and works (at least with the ps2, not sure about usb) but doesn't have drivers for my video card so i only get the kernal right now. Fedora Core 4 gives me a kernal panic - synch error. Linux really doesn't like my machine.

Also, I've attempted to update my bios. The award flash reads the floppy and displays the file, says please wait, after awhile stops reading the floppy, but endlessly says please wait. I tried flashing it from windows but the utility doesn't support windows 64bit.

---

