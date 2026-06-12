---
title: "Installed Ubuntu on USB...no more windows"
date: 2010-02-06
forum: General Help
---

### Post by VoiceInTheDesert on 2010-02-06
So I installed Ubuntu on a USB drive (32gb) and all was working fine and dandy until I decided that I wanted to reboot back into windows to get some stuff from over there. 

When I booted into Linux the first time, I saw the GRUB utility. I assume (linux noob) that this is the boot manager for ubuntu, so I shrugged it off. The problem now though is that if I don't have the stick plugged in, the computer says "GRUB failed" and gives me a "grub recovery" command line. It just hangs there and will not boot to either windows or the obviously absent linux install. 

I have a few problems with this

1. I do not want my Windows install to depend on having this USB drive on my person at all times. 
2. I do not like GRUB handling this in the first place because (at least running from my usb drive), it loads much much slower than Windows normally boots. 

How I would like this to work:

I would like to just be able to plug in the flash drive and have the choice of boots when I turn on my computer. The Mobo obviously supports booting from USB, so I was hoping it would just select by priority rather than have this dependence on the USB stick being plugged in. The whole point of having the Ubuntu on the stick was so it could be transfered back and forth from my laptop to desktop and let me work in both places...so if I can't do that and have easy access to my windows boots on both machines, I'm gonna be bummed. 

So...is there a fix for this? I have to believe that this is not the only way this will work...

Thanks in advance to anyone who can help.

---

### Post by labinnsw on 2010-02-13
You should be able to use your windows CD to fix the MBR

> Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

I had to use this on a PC that I had corrupted the MBR with by using a boot manager.

Worked perfectly. This may have been posted before, and if so, forgive me. If not, now you know how to repair your MBR. By the way MBR stands for Master Boot Record. THis procedure kind of replaced Fdisk I think.
Taken from [http://www.techzonez.com/forums/archive/index.php/t-3975.html](http://www.techzonez.com/forums/archive/index.php/t-3975.html)

You may also want to ensure that when you computer boots, it does so looking for the boot sector in the following sequence.

Floppy (If you have one)
CD
USB
Hard Disc
Network.

---

