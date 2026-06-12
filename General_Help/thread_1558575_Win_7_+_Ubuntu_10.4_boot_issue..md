---
title: "Win 7 + Ubuntu 10.4 boot issue."
date: 2010-08-22
forum: General Help
---

### Post by kszaq on 2010-08-22
Hi!

I had recently installed ubuntu alongside my Windows 7, with GRUB 2 serving as my bootloader. I can boot to both OS', however there is one problem. Everytime I boot into ubuntu, my **next** boot into Win 7 fails. It get's to 'Starting Windows...' screen and right after the windows logo animation begins a bluescreen flashes and my laptop restarts. Then when I boot to Win 7 again it states that the system had problems while starting, but everything works fine when I select to start the system as normal. After this the problem is gone for as long as I don't boot into ubuntu again.

I guess this is a strange issue and my description of the problem might not be too helpfull, but any help would be appreciated and I will do my best to provide any info You might need to help me solve this.

---

### Post by anirudhtomer on 2010-08-22
hey if on that blue screen any text is written then put a screen shot of that. It will make things clearer.

---

### Post by dougalkerr on 2010-08-22
Maybe next time you are in Ubuntu you could run 'sudo update-grub'
Maybe this will help to clean things up in case Grub did nopt configure properly and is reseting itself when you boot into Ubuntu - or something like that.
Won't do any harm anyways...

I presume you can see your Windows drive from Ubuntu?

---

### Post by elliotn on 2010-08-22
Same problem here, me wheneva I boot into ubuntu when I go and boot to windows 7 my win7 boot is always corrupt I have to repair startup

---

### Post by Sef on 2010-08-22
How did you partition the hard drive?

---

### Post by kszaq on 2010-08-22
> hey if on that blue screen any text is written then put a screen shot of that. It will make things clearer.There is some information but it flashes for about half a second and then my computer restarts. I can't manage to get any info from there :/

> Maybe next time you are in Ubuntu you could run 'sudo update-grub'Tried, it didn't help.

> I presume you can see your Windows drive from Ubuntu? Yes.

> How did you partition the hard drive?I used disk management from windows administrative tools. Shrinked my windows drive, creating unused disk space. Then during install ubuntu detected that space and allowed me to use it as it's partition.

---

### Post by dougalkerr on 2010-08-22
I presume the SWAP partition set-up okay?

---

### Post by kszaq on 2010-08-22
> I presume the SWAP partition set-up okay?It's present when I run Disk Utility:
- Partition Type: Linux Swap (0x82)
- Device: /dev/sda6
- Capacity: 5.7 GB.
Disk Utility also states that the disk is healthy.

Do I need to check anything more about it?

---

### Post by dougalkerr on 2010-08-22
Where did you install Ubuntu from? LiveCD through Windows or straight from the LiveCD at boot?

It sound a little like the Master Boot Record is getting screwed (maybe there are two and each one is getting rewritten at each boot/Login).

Is it a bother to install Ubuntu again? This is what I would do and is probably the quickest thing to do.

Can your computer take the latest version of Ubuntu as it seems to be the most stable so far.

I have been running Ultimate Edition for the last few months with no problems whatsoever.
Although this doesn't help with the boot problem but, like I say a fresh install may just sort things out.

When you get to the Partition manager delete your Linux and SWAP partitions and reallocate them as before giving your SWAP partition twice the amount of RAM that you have and then just an ext3 or ext4 partition for Linux and maker the mount point /
That should do for a fresh simple install.
Hope this helps...

---

### Post by Quackers on 2010-08-22
Boot into Windows then go to Control Panel, then System and Security, then System, on the left click on Advanced System settings, then in the Starup and Recovery section click on Settings, then uncheck the box next to Automatically restart. Ok your way out.
This will stop the system automatically rebooting when the Blue Screen appears. You can then take a photo of it and post it in this thread. It will probably be a STOP error and have numbers something like 0x7dyyyyyy

---

### Post by kszaq on 2010-08-23
> Where did you install Ubuntu from? LiveCD through Windows or straight from the LiveCD at boot?I installed it via usb stick (universal usb installer) - stuck it in, rebooted, chose to boot from usb in bios and selected to install when the menu appeared.

> It sound a little like the Master Boot Record is getting screwed (maybe there are two and each one is getting rewritten at each boot/Login).This might be a clue: I used to run openSUSE 11.2 with dual boot from grub before. However, I think I uninstalled it in a most appropriate way. First I restored windows' original mbr using it's install disc and recovery tools (recovery command line, either 'bootrec.exe /fixmbr' or 'bootsect.exe /nt60 C:\' did the trick, I don't remember now). Then, when grub got removed and my laptop was booting straight into windows, I removed all linux partitions using disk management in administration tools and merged freed up space into my windows 7 partition.
As far as I know this is the most clean and proper way to remove dual boot linux, but I might be wrong and missed something important along the way.

> Is it a bother to install Ubuntu again? This is what I would do and is probably the quickest thing to do.It's a newly deployed system, I didn't do much installing/configuring there, so if different solution wouldn't be found I'll have no other choice but to do reinstall.

> Can your computer take the latest version of Ubuntu as it seems to be the most stable so far.If by 'can it take' You mean hardware requirements then yes, I have 4gb ddr3 ram, 2.66 ghz core 2 duo, nvidia geforce 9400m g.

> Boot into Windows then go to Control Panel, then System and Security, then System, on the left click on Advanced System settings, then in the Starup and Recovery section click on Settings, then uncheck the box next to Automatically restart. Ok your way out.Thanks for the tip! Here's the pic of the bluescreen: [http://img10.imageshack.us/img10/4290/dsc00407.png](http://img10.imageshack.us/img10/4290/dsc00407.png)

---

### Post by kszaq on 2010-08-28
Bump.

I reinstalled my ubuntu. Fresh installation, no changes/updates. The problem is still there. Maybe I did something wrong during install? I told ubuntu installer to use longest unused space (which I freed up from windows disk management). Grub got set up at /dev/sda. Is that setup ok?

I didn't have this problem while using openSUSE. However, I got used to ubuntu at work and would like to use it at home as well, so it would be bummer if I had to switch to a different linux distro just because of that.

---

