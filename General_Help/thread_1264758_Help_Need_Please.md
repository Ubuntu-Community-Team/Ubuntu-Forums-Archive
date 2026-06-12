---
title: "Help Need Please"
date: 2009-09-12
forum: General Help
---

### Post by tjhooker on 2009-09-12
Ok so today my Dad drops off this laptop that he got from my stepmothers Dad. It is a Fujitsu Lifebook, N Series. The back of it has a sticker saying it came with Windows XP Home Edition. He brought it to me to fix it because I can fix desktop computers. Not too knowledgeable about laptops though but anyway lets get to the point.

The screen on the actual laptop doesn't display anything, so I plug it into my monitor. Eventually it will load up to the OS.. only it's not Windows, it's Ubuntu. I am taking a Linux class right now but it's early in the semester and we only just installed it last week. But anyway, I didn't know the username and password information to log in.

Fast forward an hour or so later, and I read up enough info that I was able to make a live CD, boot to a command line, view the username, and reset the password. Awesome. So I boot back to the Ubuntu login screen and login. No more username/password error. Only now my monitor goes blank and I am getting nothing from the laptop. What could make it run fine at the login screen and the command line but mess up when I actually try to log in? And could the fact that the laptop is running Ubuntu be what is causing the laptop screen to not work?

The list of available boot options only showed 4 Ubuntu options and a memory test or something? So I don't even know if Windows is still installed on this thing or not. Is there ANYTHING I can do with this thing?

---

### Post by NoaHall on 2009-09-12
Yes. You can use the live disk to access and copy the files(or the terminal via recovery mode if you know how) to somewhere else, then reinstall. Or go to the terminal and type "sudo dpkg-reconfigure xserver-xorg". You'll need to enter the password there. When copying the files, you should only take the "/home/" folder.

---

### Post by PeEllAvaj on 2009-09-12
If there is nothing you need to recover from the HDD of the laptop, I would recommend a complete reinstall.

If you need to recover the currently installed system, you will have to try resetting the user profiles. The easiest way to do this is to remove/rename /home/username/.  I have had problems in the past where the compositing enabled on the user profile, causing the user to be unable to login.  You should also check /var/log/Xorg.0.log to see what is happening to X.

Hope this helps.

---

### Post by tjhooker on 2009-09-12
> **NoaHall said:**
> Yes. You can use the live disk to access and copy the files(or the terminal via recovery mode if you know how) to somewhere else, then reinstall. Or go to the terminal and type "sudo dpkg-reconfigure xserver-xorg". You'll need to enter the password there. When copying the files, you should only take the "/home/" folder.

What does this do exactly?

And does anyone know why the monitor would stop working as soon as I log in?

---

### Post by NoaHall on 2009-09-12
It rebuilds the file which controls "xserver" which is what the GUI uses to base itself on.

It's likely that he's done something to damage it.

Maybe you should try clicking the sessions button on the bottom left and changing it. See if it happens again.

---

### Post by tjhooker on 2009-09-12
> **NoaHall said:**
> It rebuilds the file which controls "xserver" which is what the GUI uses to base itself on.

It's likely that he's done something to damage it.

Maybe you should try clicking the sessions button on the bottom left and changing it. See if it happens again.

Ok so how can I do this? I don't know how to use a terminal or whatever.

---

### Post by NoaHall on 2009-09-12
The sessions thing is on the same GUI as where you log in.

Terminal -

Boot up -> At grub, choose recovery mode/single user mode -> choose "drop to root shell" -> Enter the command I gave you.

---

### Post by tjhooker on 2009-09-12
It's asking me about autodetecting and giving me an option. I don't want to screw anything up any further so should I click yes or no?

---

### Post by NoaHall on 2009-09-12
Just click yes. running that command won't cause any more damage.

---

### Post by tjhooker on 2009-09-12
It got to the end I guess but just brought me back to the command line. Did I do something wrong? I rebooted and the same problem happened, login screen loaded and displayed fine but as soon as I logged in, no more display. I'm going to try it again but right now it's checking something, currently at 40%.

Is there a way to just wipe this all out and fresh install, if need be?

And am I right in assuming that since there was no Windows on the list at boot, Windows is not on this machine?

---

### Post by P4man on 2009-09-12
Before wiping it, perhaps you want to ask the owner if there are files that he wants retrieved?

If not, then yeah,  just do a fresh install from a live CD. Tell the installer to use the entire disk, and it will it all clean for you. Its hard enough to fix your own mistakes, never mind those of someone else on a OS you've never used :)

However, Im a bit worried a fresh install will give you the same problem, but if so, at least we know its a fresh install and we can rule out all other causes and talk you through it.

---

### Post by tjhooker on 2009-09-12
Ok so I finish that Xserver command and it says this:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/xii/xorg. (something here but god my handwriting is terrible)

I changed the session from "last session" to G.N.O.M.E. is that what I should have done? There was also KDE, failsafe GNOME and one other.

Changing session to GNOME results in same thing. Seems like it will log in, then the signal is no longer detected by my monitor and it auto switches to DVI (my PC).

I think I might have hit "suspend" earlier just twiddling with options. Could this have done anything?

---

### Post by P4man on 2009-09-12
> **tjhooker said:**
> Ok so I finish that Xserver command and it says this:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/xii/xorg. (something here but god my handwriting is terrible)

close enough. It was /etc/X11/xorg.something ;)

> I changed the session from "last session" to G.N.O.M.E. is that what I should have done? There was also KDE, failsafe GNOME and one other.

Try failsafe gnome
> 
Changing session to GNOME results in same thing. Seems like it will log in, then the signal is no longer detected by my monitor and it auto switches to DVI (my PC).

I think I might have hit "suspend" earlier just twiddling with options. Could this have done anything?

Nah, it seems like the monitor isn't detected properly. After logging in, if the screen still turns black, try this: press control+alt+F1. Does it give you a fullscreen terminal?

---

### Post by NoaHall on 2009-09-12
Don't worry about suspend. If you can get to a terminal, do this -

```
 ls /etc/X11/ | grep backup 
```

This will help us to see if the xserver settings have been backed up.

Note - these commands/filenames are case sensitive.

---

### Post by tjhooker on 2009-09-12
Ok I changed the session to KDE and that got me to the desktop. Doesn't seem like there is really anything on this machine. Like someone installed Ubuntu on it then just left it. Maybe because of the laptop screen problem? Could installing Ubuntu make the screen stop working? Maybe it's an incompatibility/driver issue or something?

Anyway, I hit Control + Alt + F1 to bring up a terminal but it kept spamming this error:

CDROM (ioctl) error, command   Test Unit Ready

So I used F7 to get out of it.

---

### Post by NoaHall on 2009-09-12
Ah, so kde runs fine? That's great. Run "sudo apt-get remove --purge gnome" from a terminal. I think it's called something like "kterm" on kde. Also run the previous command I gave you.

---

### Post by P4man on 2009-09-12
> **tjhooker said:**
> Ok I changed the session to KDE and that got me to the desktop. Doesn't seem like there is really anything on this machine. Like someone installed Ubuntu on it then just left it. Maybe because of the laptop screen problem? Could installing Ubuntu make the screen stop working? Maybe it's an incompatibility/driver issue or something?

Anyway, I hit Control + Alt + F1 to bring up a terminal but it kept spamming this error:

CDROM (ioctl) error, command   Test Unit Ready

So I used F7 to get out of it.

Well, a quick google on that error suggests the cdrom drive is defective. But you used it to boot an ubuntu cd, or didn't you?

as for the monitor, its probably a matter of configuring it right. Happens occasionally when you install videocard drivers that they set wrong resolution, refresh rate or color depth, making the screen go black. can be a bit of pain to cure, but its certainly doable :)

---

### Post by tjhooker on 2009-09-12
Ok on the gnome purge it says gnome was not installed so it was not removed.

On the earlier one, nothing at all happens when I type it in. Let me make sure I typed it right:

ls /etc/X11/ | grep backup

---

### Post by NoaHall on 2009-09-12
Ah, there's your problem then! He's deleted the gnome!
run "sudo ldconfig"

Yes, you got it right, and that tells us that there's no back-up. So that means it will have to be made from scratch. This is easily set up on Ubuntu (as opposed to on Arch or something, where you have to make your own).

---

### Post by P4man on 2009-09-12
> **NoaHall said:**
> Ah, there's your problem then! He's deleted the gnome!
run "sudo ldconfig"

Yes, you got it right, and that tells us that there's no back-up. So that means it will have to be made from scratch. This is easily set up on Ubuntu (as opposed to on Arch or something, where you have to make your own).

Why does he need it? Seems KDE works fine, why bother with the xorg.conf? These days its pretty much empty anyway, only needed if something aint working right. BTW, xorg.conf backups no longer end with.backup , but with the date.time I think. Thats why your grep isnt finding anything
Just try 

```
ls /etc/X11/ 
```

Its not like there are 1000 files in there. Probably not even 10 :)

---

### Post by tjhooker on 2009-09-12
That command asked for a password but idk if it actually did anything after I typed in the password.

---

### Post by tjhooker on 2009-09-12
ls /etc/X11/  brought back some sort of list of files.

app-defaults           xinit          xserver
cursors                  xkb           Xsession
default-display-manager  xorg.conf    Xsessiond

Among a few others. What does this mean?

---

### Post by NoaHall on 2009-09-12
In the terminal, it doesn't show if you are writing a password. Just type in the password and press enter.

@P4man 

He needs it because it will help the monitor set-up in general. It's still "xorg.conf.backup" for me. Maybe it's cause I have nvidia, and that's what nvidia-xserver does.

---

### Post by tjhooker on 2009-09-12
Yeah I mean I entered the password and hit enter but then nothing happened.

---

### Post by NoaHall on 2009-09-12
It's listing the files in that map - xorg.conf are the ones we want.

It looks like nothing happened, but accutally, it's cleaning up the links the system has made.

---

### Post by tjhooker on 2009-09-12
Cool. So what should I do next?

I found some files (including naughty stuff) so I guess someone was using the computer with Ubuntu installed after all.

---

### Post by NoaHall on 2009-09-12
Well, run lspci and post the output here so we can see what graphics card it has.

---

### Post by tjhooker on 2009-09-12
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:09.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
00:09.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

---

### Post by NoaHall on 2009-09-12
Ah, ATI. The dreaded foe (currently) of Linux. Well, that's probably why your display isn't working so well. Anyway, you have KDE, so just keep to that, and make it the default session :)

---

### Post by tjhooker on 2009-09-12
So there's no way to get the laptop screen working with this? I don't know if they have another monitor to hook this laptop up to at their house.

---

### Post by tjhooker on 2009-09-12
Also, is there a way to tell if Windows is still on this thing?

---

### Post by NoaHall on 2009-09-12
Well, if it's not a option at GRUB, then it's probably not there. However, if there's any disk that can be mounted, then it might be on there.

---

### Post by tjhooker on 2009-09-12
> **NoaHall said:**
> Well, if it's not a option at GRUB, then it's probably not there. However, if there's any disk that can be mounted, then it might be on there.

How would I find this out? Sorry I am so clueless.

---

### Post by NoaHall on 2009-09-12
Run "mount -l"

---

### Post by tjhooker on 2009-09-13
Ok new question.

I have a Windows XP disc and want to do a dual boot. But if I boot up with the Windows disc in the CD drive, it still boots to Ubuntu. How can I access the disc in the drive while in Ubuntu?

---

### Post by sailthesea on 2009-09-13
> **tjhooker said:**
> Ok new question.

I have a Windows XP disc and want to do a dual boot. But if I boot up with the Windows disc in the CD drive, it still boots to Ubuntu. How can I access the disc in the drive while in Ubuntu?

If you want to set up a dual boot you would be best installing XP first over your whole disk then using the Ubuntu Live CD get Gparted to create a couple of new partitions for your Ubuntu OS and a perhaps a home and swap partition as well depending on you machine Then install Ubuntu from CD Windows likes to be first on the drive though As you have all the CDs you need and no need to rescue any data from the machine it should be a simple learning experience and no big deal if things go wrong the first time 
 Google around for a guide on dual booting your machine and read carefully
 The ATI issue can be worked around but it is a problem area with Ubuntu
Good luck:)
 EDIT To boot into the windows CD try F11 or F8 at startup Or you may have to edit the bios

---

### Post by tjhooker on 2009-09-13
Yeah that's the thing.. the PC boots directly into the Ubuntu boot menu. I can't F8 or 11 or edit BIOS. That was my first though, but none of it loads.

---

### Post by sailthesea on 2009-09-13
Strange 
Is the optical drive working ? Will a Ubuntu LiveCD boot up and which version are you trying?
Also are you using a CD as opposed to  DVD I've made the mistake of trying to use a DVD in a CD drive:confused:

---

### Post by tjhooker on 2009-09-13
I just made a Live CD and restarted and it booted to the CD. But it won't boot to the Windows CD. It boots right into Ubuntu and won't let me edit BIOS.

---

### Post by sailthesea on 2009-09-13
You could uninstall ubuntu via the LiveCD and have a better shot at putting windows back up from boot it sounds like grub has taken over the MBR and your disk is written ext3/4 so windows wont work Once you clear the disk you should be able to install windows and progress

---

### Post by tjhooker on 2009-09-13
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

I downloaded from that link, I don't see any options to uninstall. Would you happen to know where it is?

---

### Post by sailthesea on 2009-09-13
Really don't get why your windows disk won't install
Sorry I must sleep ZZz

---

### Post by tjhooker on 2009-09-13
Ugh this thing won't even boot to the freaking Ubuntu disc now WTF.

---

