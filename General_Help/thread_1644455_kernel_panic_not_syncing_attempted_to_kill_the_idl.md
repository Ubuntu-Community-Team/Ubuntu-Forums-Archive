---
title: "kernel panic not syncing attempted to kill the idle task wubi ubuntu install"
date: 2010-12-13
forum: General Help
---

### Post by Milorandom123 on 2010-12-13
-I am completely new to Linux / Ubuntu.
-I am running Windows Vista
 

I just downloaded Wubi - To install Ubuntu on my computer. (Whether  it's called Dual boot or running Ubuntu inside of Windows Vista I do not  know.) Everything went fine, got a very easy little screen to ask what  partition I wanted to install it on and how much size, etcetera, the  download went fine, blablabla.
 

Problem: It asks me to reboot (This is the first reboot I got.), I  say yes, it reboots, I get the booting screen where I get to pick  between Windows and Ubuntu, I pick Ubuntu, and it gives me this 'error'.
 

Among other things it reads
'Kernel panic not syncing attempted to kill the idle task'
It ends with something like
'x86_64_start_kernel_ -'
 

After this nothing happens - I waited about 25 minutes.

I manually turned off my computer - started it up again - once again chose Ubuntu and the same problem occured.
 

Hope you guys can help this current rookie out,
-Thanks in Advance.


1. I looked around the Ubuntu folder inside my C a little, it shows the iso file as Ubuntu-
10.04.1-desktop-amd64
2. Some other forum advised people with this problem to check their RAM, so  I unplugged both, cleaned and switched them. (I have 2 GB ram total.)  This didn't work. Same problem still occurs.

---

### Post by Rubi1200 on 2010-12-13
Hi and welcome to the forums :)

For general information, Wubi issues and solutions, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

I do not know this particular error, and if there is anything in the thread I linked to that is not clear, come back here and ask.

Also, post the specifications for the machine in question.

Thanks.

---

### Post by MrFaler on 2010-12-13
Asking the obvious, but you do have a 64-bit capable processor? The amount of RAM you have suggests otherwise.

---

### Post by Milorandom123 on 2010-12-13
@Rubi: Reading through it now. Thanks.

@MrFaler: Could that be it? I mean, Wubi automatically started to download that one, so I thought that it had somehow scanned my system and concluded that was the right one for me.

--- 

@Rubi: Not too sure what all full under 'specifications', but dxdiag gives

OS: Windows Vista(^tm) Home Premium (6.0, build 6001)
Language: Dutch
Model: MS-7235
BIOS: Phoenix AwardBIOS v6.00PG
Processor: Intel(R) Core(TM)2 CPU 6300 @ 1.86GHz (2 CPUs), ~1.9GHz
RAM: 2046 MB RAM
DirectX 10

DxDiag 6.00.6001.18000 32-bits Unicode

Does that show you guys anything?

---

### Post by Milorandom123 on 2010-12-13
By the way, could it be that this problem is fixed if I just install it in the 'standard' way? 
So through: 'http://www.ubuntu.com/desktop/get-ubuntu/download'

---

### Post by Rubi1200 on 2010-12-13
If you click on the link to the Wubi Guide near the beginning of the thread, I think you will find the explanation near the top of the guide.

This can be fixed of course, but first finish reading the information.

Let me know if you need anything else.

---

### Post by Rubi1200 on 2010-12-13
> **Milorandom123 said:**
> By the way, could it be that this problem is fixed if I just install it in the 'standard' way? 
So through: 'http://www.ubuntu.com/desktop/get-ubuntu/download'
Could be. I haven't taken a close look at the ISO recently, but I believe the Wubi installer is still on it by default.

Is Wubi installed? Can you boot Windows?

---

### Post by Milorandom123 on 2010-12-13
I think my problem falls under:
[SIZE=1]
*"*[/SIZE][I][SIZE=1]**Problem #2:**

You have Wubi installed and are able to boot Windows normally. [/SIZE][SIZE=1]

However, attempting to boot Ubuntu leads to a number of possible failures including, but not limited to, the following:[/SIZE][SIZE=1]

computer reboots without user interaction, a black screen with or  without any error messages, loadfont errors, file not found errors, and  the like."[/SIZE][/I]    

Problem is, with:
[I][SIZE=1]"[/SIZE][SIZE=1]**Solution #1 (10.04):**

If it is a 10.04 install, the fix is to boot an Ubuntu LiveCD, loop  mount the wubi root.disk and manually edit the grub.cfg file."[/SIZE][/I] 
Because I'm installing through Wubi I haven't heard of an 'Ubuntu LiveCD', is that just that version burned on a CD or USB, as the normal download function suggests I do?

And yes my Windows is running perfectly fine. 

--- --- --- --- --- 

What I did so far though is completely remove Ubuntu from my system and I'm know trying the normal download option. Just finished formatting my USB to Fat32 as was adviced (Never even knew that existed, another lesson learned.). Wonder if that fixes the problem. I'll let you know how it goes.

---

### Post by Rubi1200 on 2010-12-13
A LiveCD (or USB) means the ISO image has been burned or installed on one of these media for usage.

Let me know what happens.

---

### Post by bcbc on 2010-12-13
If it's failing on the first reboot - then Ubuntu is not installed yet. So there's no 'install' to fix.

Wubi.exe runs in windows, collects required info (username, password, timezone, language), creates the virtual disks (unformatted), then set instructions for the Ubuntu installer. 
On the first reboot, the installer runs with those settings - formats the virtual disk and installs Ubuntu to it.

So you're getting stuck when it's starting up Ubuntu to run the installer. Which should be similar to running a live CD.
To confirm this - did you see some text saying:
> Completing the Ubuntu installation
For more installation options, press ESC now...


I have no idea why it's failing - wubi does check whether you're capable of running 64-bit (you can force it to run 32-bit if you want to). 

wubi.exe also checks md5 checksum of the .iso before it installs, so that rules out a corrupt installation image. But maybe if your drive is very fragmented it could be causing issues. So run a couple of defrags - a good idea anyway.

PS if you get it installed, please do not upgrade packages grub-pc and grub-common - known to fail as per Rubi1200's Wubi Megathread.

---

### Post by Milorandom123 on 2010-12-13
While I'm fixing another problem that just came up (no worries, I actually do know how to fix this one.) I'll say that I did 'burn' the latest Ubuntu version on a USB (first I formatted it to Fat32) though while restarting my PC, with that USB plugged in, nothing happened and it just went straight to windows. (Like I said previously, I did completely uninstall ubuntu.) Afterwhich I got that formentioned problem I'm working on now. In a little time I'll troubleshoot a little myself as to why the USB didn't take, we'll see. (Though I might just go and burn it on a CD anyways, seemed to be the playing-it-safe option.) 

bcbc, oh okay. I did indeed see "Completing the Ubuntu installation
For more installation options, press ESC now..." Or something extremely similar to it. Running a defrag now. To be honest, I am guilty of having this PC for close to 3 or 4 years and I don't think I've ever defragmented it. (And I do use it extensively.) 

Is running several defrags in a row beneficial? Or will one defrag pump it up to full possible efficiency? 

I'll keep at it till it works. About a year ago I tried the very same thing and I lost my entire hard drive after which I quit, but this time I'll keep going till it works. Really want to have this thing done. I'll let you know.

---

### Post by bcbc on 2010-12-13
I've never used Vista... so I can only say what I know with XP:
yes, you can defrag more than once. It shows you how defragmented it is each time - it also tells you which files cannot be defragmented. Sometimes you can get around this by copying these and removing the original or using a backup media e.g. external usb drive to temporarily remove large files. Also turning off system restore prior to defragmenting can sometimes help - but use with appropriate caution - as you lose all restore points (best to do when you know you've got a stable system).

I recommend searching on Microsoft's support site for help.

PS to boot from USB you usually have to change the boot order via the BIOS, either go into the BIOS settings, or override at startup with the boot options key.

---

### Post by Milorandom123 on 2010-12-14
Little update:
Haven't given up yet,

problem 1: I have a USB Keyboard - It's a little weird, because I actually did get it to work during boot up a few months ago, but after simply replugging it in the exact same USB port it doesn't work AT ALL (not even in Windows), and I have to plug it in a different set of USB ports, with which it only works in Windows. (Sadly I don't have one of those old keyboards lying around.)
-I think I'll be able to fix this myself though. I don't know the technical terms but I still have some things to try out.

problem 2: It doesn't seem to boot from the CD. [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD) states it could be the BIOS (the CD was properly burned), which takes us back to problem 1. 

Let you know when it's fixed and I actually get the CD to boot and run.

---

### Post by Milorandom123 on 2010-12-14
nvm

---

### Post by Milorandom123 on 2011-01-22
Quick update (felt like I owed it to you guys who helped me out there.);


While trying to fix this, I encounter several other problems, and while trying to solve them, end up frying my motherboard. Long story short, got new motherboard, tried out and installed ubuntu via USB (after fucking around in boot menu) no problem so far. 

Finished installing a few hours ago. 

So even though this problem wasn't solved, I should thank you for your help, I might've just given up altogether back then without your input. 

-MR123

---

