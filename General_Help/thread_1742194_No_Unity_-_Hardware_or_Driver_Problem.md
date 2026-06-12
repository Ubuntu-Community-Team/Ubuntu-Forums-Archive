---
title: "No Unity - Hardware or Driver Problem?"
date: 2011-04-28
forum: General Help
---

### Post by dniMretsaM on 2011-04-28
I just installed 11.04 and when I logged in, it told me that I do not have the hardware required to run unity. Is this an actual hardware problem, or is it just that I don't have the right drivers? If it's a hardware issue, how do I know what I don't have. If it's a driver thing, how do I know what driver I need to install.

---

### Post by coffeecat on 2011-04-28
It probably means that you don't have a graphics card/driver combination that will support 3d. Unity is a compiz plugin and needs 3d. As a gross oversimplification:

Most Intel graphics will work out of the box.

Many ATI cards will work out of the box with the default open source driver. Some will need the proprietary fglrx driver.

Nvidia cards will not give you Unity with the default open source nouveau driver. You have the choice either of using an experimental package to enable 3d with nouveau or installing the proprietary nvidia driver.

To repeat - this is a generalisation. Which graphics chipset do you have?

**EDIT**: to find if you need a driver installed, and seeing that the system has defaulted to classic gnome, go to System > Administration > Additional drivers.

---

### Post by dniMretsaM on 2011-04-28
I don't know what chipset I have so I'll post the output of lspci:
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```

As for drivers, there are none listed in the Additional Drivers menu.

---

### Post by KegHead on 2011-04-28
Hi!

You could goto classic:

system..admin..login...choose classic and restart.

That's what I did.

KegHead

---

### Post by dniMretsaM on 2011-04-28
But I don't want to use classic. Unity is more appealing to me. If I can't get it to work, I'll probably be migrating to Kubuntu or Xubuntu. I may try GNOME 3 and/or LXDE.

---

### Post by Mashepherd on 2011-04-28
For what its worth, I spent the best part of my day today messing around with drivers.

When I initially installed 11.04 it told me the same thing, that I didn't have the hardware necessary to do the unity thing, so I installed the proprietary nvidia-current driver and that completely naffed up my system but then tried nvidia-173 i think and it seemed to work fine, i mean it tells me that the driver is activated but "not currently in use" but unity works ok.

---

### Post by slowtype on 2011-04-28
I am having a difficult time enabling unity as well.  

I have a nvidia 7400 go in my laptop and the 173 driver installed.  

The driver message states that it is activated but not in use.

---

### Post by slowtype on 2011-04-28
just found out its because my video card has been blacklisted because it has issues with unity.

---

### Post by nicknormal on 2011-04-29
oh why do I upgrade right away! now my laptop flashes the ubuntu logo on the purple background and then the screen just goes black. no response.
if I hit ctrl+alt+del it reboots, but other than that it's hung on bootup.

---

### Post by coffeecat on 2011-04-29
> **dniMretsaM said:**
> I don't know what chipset I have so I'll post the output of lspci:

From your lspci output:

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

That's a very old chipset. The chances of getting Unity with that may be slim. There is once possibility you might want to try. In this thread:

[http://ubuntuforums.org/showthread.php?t=1725201](http://ubuntuforums.org/showthread.php?t=1725201)

The OP has the later 855GM chipset and posted a link to a fix for that one in post #22. Whether that will work for the 845G, I don't know.

---

### Post by EddieGal on 2011-04-29
> **slowtype said:**
> I am having a difficult time enabling unity as well.  

I have a nvidia 7400 go in my laptop and the 173 driver installed.  

The driver message states that it is activated but not in use.
Same problem here. Tried with the recommended and 173. None work

---

### Post by AliG112 on 2011-04-29
I have a similarly old intel driver but installing the 2d version of unity worked for me.

```
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
sudo apt-get update
sudo apt-get install unity-2d-default-settings

```
Then choose unity 2d on login.
Hope it helps.

---

### Post by dniMretsaM on 2011-04-29
> **coffeecat said:**
> From your lspci output:

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```That's a very old chipset. The chances of getting Unity with that may be slim. There is once possibility you might want to try. In this thread:

[http://ubuntuforums.org/showthread.php?t=1725201](http://ubuntuforums.org/showthread.php?t=1725201)

The OP has the later 855GM chipset and posted a link to a fix for that one in post #22. Whether that will work for the 845G, I don't know.

Yeah, I knew it would be old. This computer is from like 2003. Everyone else in my family has nearly brand new laptops and I'm stuck with this...
> **AliG112 said:**
> I have a similarly old intel driver but installing the 2d version of unity worked for me.

```
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
sudo apt-get update
sudo apt-get install unity-2d-default-settings

```Then choose unity 2d on login.
Hope it helps.

Ok, if I can't get 3d to work, I'll use this. Thanks for the tip!

---

### Post by dniMretsaM on 2011-04-29
I manually enabled the Intel driver so how do I tell it I want to login into Unity instead if GNOME?

---

### Post by grahammechanical on 2011-04-29
The driver activated but not in use message means that you are not using 3D effects. I have that message on 11.04 but in 10.10 the message is driver activated and in use. The difference? Enhanced visual effects in 10.10 but Unity 2D in 11.04.

Regards.

---

### Post by dniMretsaM on 2011-04-29
I have never gotten that message.

---

### Post by Frogs Hair on 2011-04-29
I use an Nvidia graphics card and all I had to do is install the recommended proprietary driver while in Classic Gnome and reboot.

---

### Post by dniMretsaM on 2011-04-29
Well la de da for you. Lol. I really need to get a new computer but I don't have the $$. Neither do my parents.

---

### Post by Bristol_Green on 2011-04-29
I got the same message after installing Natty. So I activated the NDIVIA driver, and now have no Unity and no top panel. In fact nothing at all except the background screen, attractive though it is! The led indicates some HDD activity, but nothing visible on screen.

When I left-click the mouse, a folder icon appears very briefly. It is labelled 'untitled folder'.
Other items also flash onto the screen and disappear. How can I get rid of this driver and revert to 'classic'?

---

### Post by dniMretsaM on 2011-04-29
@Bristol_Green: Try deactivating the driver.

Ok, so I decided to not worry about 3D and just go with the 2D version of Unity. How can I uninstall the Unity 3D and GNOME since I don't want them? And I'm still not sure how to select what environment I wan to log in with.

---

### Post by whitefort on 2011-04-29
Same problem here - 'activated but not currently in use'.

This on a computer that was very happily running Compiz with all the bells and whistles before I made the mistake of switching to 11.04.  I can only run Ubuntu 'classic' (whoopee).  I'm lucky.  One of my friends found 11.04 left him with no GUI at all, and the other had such graphics issues with the live CD that he didn't even try an install.  

I've been a Ubuntu fan since Dapper Drake, but I can't say I'm too impressed by the narwhale so far...

---

### Post by Bristol_Green on 2011-04-29
> **dniMretsaM said:**
> @Bristol_Green: Try deactivating the driver

Well yes I would if I had any control over the screen. Instead I'm reinstalling Natty. Would it help if I got a better graphics card? My PC is over 10 years old (but I'm typing this on a fairly new netbook).

---

### Post by dniMretsaM on 2011-04-29
Try booting into command line and disabling it from there (possible?). If you can do that, it would be a lot easier than reinstalling.

---

### Post by Bristol_Green on 2011-04-29
> **dniMretsaM said:**
> Try booting into command line and disabling it from there (possible?). If you can do that, it would be a lot easier than reinstalling.

How do you boot into command line? I have made Ubuntu the only OS on my PC, so there's no GRUB screen, just the drums, then straight into linux. The reinstall has nearly completed anyway. It would be useful to know what to do if I'm daft enough to try that driver again though!

Th reinstall has completed, but same problem! no Unity sidebar and no panels. I have a mouse pointer but nothing to point at. No way of getting to Settings, or Terminal, or anywhere else. Ctrl-Alt-Del worked, but I don't know how to get into the system to make any changes.

---

### Post by dniMretsaM on 2011-04-29
Holding Shift when booting opens the GRUB menu. I believe you can boot to a command line from there.

---

### Post by Bristol_Green on 2011-04-29
> **dniMretsaM said:**
> Holding Shift when booting opens the GRUB menu. I believe you can boot to a command line from there.

Done that. 'Drop to root shell prompt' got me a command line. Now what?

---

### Post by dniMretsaM on 2011-04-29
Um, check [this thread](http://ubuntuforums.org/showthread.php?t=812323). It was for an older version, but it may work. If it doesn't, I'll do some more looking.

---

### Post by Bristol_Green on 2011-04-29
> **dniMretsaM said:**
> Um, check [this thread](http://ubuntuforums.org/showthread.php?t=812323). It was for an older version, but it may work. If it doesn't, I'll do some more looking.

Thanks, MasterMind, I'll check that out.

---

### Post by dniMretsaM on 2011-04-29
No problem. Again, just tell me if it doesn't work. I'll gladly see if I can find something else if it's needed.

---

### Post by Bristol_Green on 2011-04-29
Running in failsafe graphics mode I was able to go to System>Preferences and remove the offending driver.
Many thanks for your help, MM.

Do you think I should get a new graphics card?

---

### Post by EarlsFurniture on 2011-04-29
Hitting CTRL+ALT+F1 to F6 should also get you a tty login.  (X always runs on tty7 available with CTRL+ALT+F7) You can then log into the system again and use the CLI there.  You can also launch X again from that TTY if you so desire.  When my GUI goes down occasionally because I mucked something up, I use this and Lynx to figure out how to recover it.

Alternatively, from the GUI you can try ALT+F2 for a "Run Application" prompt. You can then give the command to launch any terminal program you have installed such as xterm or gnome-terminal.

---

### Post by Bristol_Green on 2011-04-29
I didn't know that either, EarlsFurniture. 

When I activated the experimental 3d driver, I got the Unity side bar, but *without icons!* And when I hovered over where they should have been, their labels appeared. I was able to open applications by clicking on the apparently empty space next to the label. I suppose I could work with that, but I decided it was too much trouble, so reluctantly went back to classic.

New graphics card then.

---

### Post by dniMretsaM on 2011-04-30
You could try the 2D version of Unity. Personally, I don't like it because it has way fewer customization options than 3D, so I switched to KDE (which seems pretty nice).

---

### Post by Bristol_Green on 2011-04-30
> **dniMretsaM said:**
> You could try the 2D version of Unity. Personally, I don't like it because it has way fewer customization options than 3D, so I switched to KDE (which seems pretty nice).

I've got the 2d version now, thanks. I agree it's not as nice as the 3d version I've got on my netbook, but it will have to do for now. I tried KDE about a year ago and didn't like it, so I won't be going back there.

Good to know I can always go back to classic.

---

### Post by dniMretsaM on 2011-04-30
I guess KDE is not for everyone. That's why there are tons of other options out there. Open Source FTW! I'm gonna mark this thread a solved now.

---

### Post by filster on 2011-04-30
I think it's some kind of problem with nvidia proprietary drivers. I have this same issue with Geforce Go 7300. There are many threads now on this forum with "nvidia drivers" issue. No visual effects, no Unity, can't use nvidia-current driver (but it shows as activated). It's weird.

edit: And sorry, I don't know how this is 'Solved', since we haven't found a solution to this problem, just avoided it (in a way).

---

### Post by abtrakt on 2011-05-03
> **nicknormal said:**
> oh why do I upgrade right away! now my laptop flashes the ubuntu logo on the purple background and then the screen just goes black. no response.
if I hit ctrl+alt+del it reboots, but other than that it's hung on bootup.

I had the same problem, i was booting from usb3.0, that was the problem. Try with a usb2.0 port.

---

