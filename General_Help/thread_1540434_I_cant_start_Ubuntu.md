---
title: "I cant start Ubuntu"
date: 2010-07-27
forum: General Help
---

### Post by Laeys on 2010-07-27
All I see is a black screen with the little rolling ball cursor before getting to the log on screen.  It just keeps rolling all day.  
There was no apparent cause, it just started a few days ago.  Unless it has to do with my failed remote desktop attempt.  Help please?

---

### Post by robsoles on 2010-07-28
First question to road of recovery:

Can you boot a LiveCD at this point?

---

### Post by Laeys on 2010-07-28
I can, but I couldn't find any remnants of my hard drive when I did so.

---

### Post by robsoles on 2010-07-28
Do you mean that it wasn't listed under 'Places' directly under 'computer' in the list under 'places'?

That's going to make it really painful if ***that*** is what you mean - which LiveCD are you using?

---

### Post by tarps87 on 2010-07-28
From the live cd can you post the output of
```
sudo fdisk -l
```

---

### Post by Laeys on 2010-07-28
> **robsoles said:**
> Do you mean that it wasn't listed under 'Places' directly under 'computer' in the list under 'places'?

That's going to make it really painful if ***that*** is what you mean - which LiveCD are you using?

It's a Hardy Heron CD.
Under places there is a 18.5 GB media, which I believe is the appropriate drive, but I get this message when I try to acces it:

"Unable to mount location. DBus error org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

---

### Post by Laeys on 2010-07-28
> **tarps87 said:**
> From the live cd can you post the output of
```
sudo fdisk -l
```

```
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e


Device Boot	Start		End		Blocks	Id	System
/dev/sdal		      1		    5	
	40131	de	Dell Utility
/dev/sda2		      6		2256	   18081157+	  7  HPFS/NTFS
/dev/sda3		2257		4863	   20940727+	  5  Extended
/dev/sda5		2257		4749    20024991         83 Linux
/dev/sda6		4750		4863       915673+	 82 Linux swap / Solaris
``` 
I may have messed up the formatting a bit.

---

### Post by tarps87 on 2010-07-28
Well you partitions are still there, have you tried pressing ctrl+alt+f1 once this cursor appears?

---

### Post by Laeys on 2010-07-28
> **tarps87 said:**
> Well you partitions are still there, have you tried pressing ctrl+alt+f1 once this cursor appears?

I had not tried this, but trying it now it does work, or at least I think it did.  However I've never done this before so I don't know what it is supposed to do.  It says: 
```
[  125.460921] serial8250: too much work for irq17
```

---

### Post by tarps87 on 2010-07-29
Hmm, it looks like there is a hardware/driver issue. Have you access to a live cd of the same release that you are currently using.
Also can you post the output of
```
sudo lspci
```

---

### Post by robsoles on 2010-07-29
I had to get a copy of (what I expect) your LiveCD is to be sure of what you might be able to try in a GUI before having to resort to the terminal.

Boot off your LiveCD (Hardy Heron) and go to "System"->"Administration"->"Partition Editor" and see if you can find your OS install HDD (the hard disk you usually boot from).

If you can see it then please right click it and see if the 'check' option is offered and enabled - if it is enabled then please click it and see what it tells you.

Can you open firefox off your LiveCD and try to access the forums? You might be able to get screen shots and/or copy and paste stuff for us from there.

The result of tarps87's 'code' command for terminal ran from the LiveCD could be copied and pasted, for instance, from the terminal to the browser - likely worthwhile info if we can't get anything in the GUI to fix this or enlighten us as to why it can't be fixed.

---

### Post by Laeys on 2010-07-29
from sudo lspci:

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
01:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:06.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
01:06.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```

I'm sorry, how do I know which partition is the OS install HDD? Here is what's listed:
```
Partition   File System   Size             Used                  Unused        flags

/dev/sda1   fat 16        39.19 MiB          7.17 MiB          32.02 MiB

/dev/sda2     ntfs        17.24 GiB                                                    boot

/dev/sda3   extended    19.97 GiB      

/dev/sda5    ext3          19.10 GiB       10.32 GiB              8.78 GiB

/dev/sda6    linux-swap   894.21 MiB
```
(windows xp is also installed but nobody actually uses it anymore)

I didn't mention this before because I didn't want to confuse things, but this is actually my mom's computer that I've been trying to help her with over phone/email (I live 1000 miles away) so I apologize for the delays and mistranslations etc.  Thank you for helping though.

---

### Post by robsoles on 2010-07-29
The one that is 'ext3' is more likely the Linux install than any other - that one needs checking if it can't be mounted.

---

### Post by Laeys on 2010-07-29
I was able to check the ext3 partition and it didn't seem to find any issues or run into any problems.

---

### Post by robsoles on 2010-07-29
When booted from the LiveCD your system should list all readable/mountable file systems under "Places" - please ask your Mom to have a look for the drive in there again, if it will mount then that will be handy for us.


Does the Windows OS on this computer still boot and function if it is selected?

---

### Post by tarps87 on 2010-07-30
Sorted:
[B]01:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
[/B]
This card here (your modem) is the issue, it is a known issue in Ubuntu 9.10 it may also be an issue in 10.04 but it is worth a try, if you can get a copy of the live cd

Does you Mum use the modem connection? If not we can disable it but we will need to know the computer make and model or the motherboard make and model

---

### Post by robsoles on 2010-07-30
> **tarps87 said:**
> Sorted:
[B]01:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
[/B]
This card here (your modem) is the issue, it is a known issue in Ubuntu 9.10 it may also be an issue in 10.04 but it is worth a try, if you can get a copy of the live cd

Does you Mum use the modem connection? If not we can disable it but we will need to know the computer make and model or the motherboard make and model

I wonder if you are rushing out on a limb there tarps87, to just pin it on that modem, due laeys OP - it isn't clear but the implication I see is that the system ran OK till recently.

> **Laeys said:**
> All I see is a black screen with the little rolling ball cursor before getting to the log on screen.  It just keeps rolling all day.  
There was no apparent cause, it just started a few days ago.  Unless it has to do with my failed remote desktop attempt.  Help please?

Of course no harm in disabling the modem to rule it out of the problem solving process but I get the impression that the GRUB loader (if not other part of Boot process) has fallen on it's proverbial backside in this system.

---

### Post by tarps87 on 2010-07-30
> **robsoles said:**
> I wonder if you are rushing out on a limb there tarps87, to just pin it on that modem, due laeys OP - it isn't clear but the implication I see is that the system ran OK till recently.



Of course no harm in disabling the modem to rule it out of the problem solving process but I get the impression that the GRUB loader (if not other part of Boot process) has fallen on it's proverbial backside in this system.

I'm willing to bet that there has been an update at some point and this is a reported issue that occurs after an number of reboots so it's only logical to try it. I could be wrong.

---

### Post by Laeys on 2010-07-30
She has a DSL modem, which means she isn't using the modem card? Is that right?  Is there a way to determine what the exact model is?

She's been using her netbook which doesn't have a CD drive, but I could ask her if she knows someone who could make another live CD.  Could we use the CD to update without losing the hard drive contents?

I don't know if this is relevant, but the grub menu seems to work fine; she can load the recovery menu but when trying to boot from there the blank screen appears.  She can choose to start in windows xp but I don't think that has been working for awhile now.

---

### Post by robsoles on 2010-07-30
> **tarps87 said:**
> I'm willing to bet that there has been an update at some point and this is a reported issue that occurs after an number of reboots so it's only logical to try it. I could be wrong.

You seem to demonstrate my regular attitude to such stuff so I am very glad to believe that I have not offended you by posting as I have.

> **Laeys said:**
> She has a DSL modem, which means she isn't using  the modem card? Is that right?  Is there a way to determine what the  exact model is?

She's been using her netbook which doesn't have a CD drive, but I could  ask her if she knows someone who could make another live CD.  Could we  use the CD to update without losing the hard drive contents?

I don't know if this is relevant, but the grub menu seems to work fine;  she can load the recovery menu but when trying to boot from there the  blank screen appears.  She can choose to start in windows xp but I don't  think that has been working for awhile now.

So what is happening is that the GRUB loader is handing off to the OS loader and that is falling on it's backside - I'm pretty drunk right now (soz, it's friday night where I am...) and am unwilling to believe that I can give a decent course to 'next step' let alone 'recovery' at this point/post.

tarps87 may have another idea based on that it's not the internal modem and that it is the binaries after GRUB and maybe not - I have ideas from what you are saying but won't pursue them for a minimum of eight hours from now - please stand by for another poster or myself to revisit your problem within about 12 hours from now. Sorry, I know waiting isn't easy ;)

---

### Post by robsoles on 2010-07-30
Oh, I am a drunken fool - I will try to make advice in this post as harmless as possible!!!!

Please have Mom turn/shut the machine completely off and wait a minimum of about 15 seconds after it has completely become inert.

After pressing the 'on' or 'go' button, please have Mom press and hold the [Shift] key - better still if she waits till after POST (Power On Self Test) but most Motherboard BIOS won't complain about [Shift] key hence the choice - this should offer the OS booting menu in it's entirety and from there I want Mom to choose the recovery menu, if it is available I want her to take the trouble to list the options to you and you to list the options to me.

Maybe pointless and when I sober up in 8 hours I may apologise for putting you and Mom to bother but one of the choices may become the course we follow to get it fixed for you/her

Meaning to be harmless,
Yours,
robsoles (:))


here is edit: Mom can simply press and hold the power button for about 3 to 5 seconds to have the machine power itself down again to avoid having to take one of the choices off the recovery menu - this boot-up is not intended for off the LiveCD but off the HDD, I think you probably got that but I realise I didn't specify....

---

### Post by robsoles on 2010-07-30
OK, now I am at least sober if not actually thinking any clearer than last night ;)


We need to rule out that modem to be sure tarps87 isn't right about it being the source of the problem - Can it be removed or if it is built-in to the system then can it be disabled in BIOS?


Once booting has been tried with that modem removed from the equation it will be handy to get a look at a couple of log files off the machine in question but it will mean mounting that hard drive.

---

### Post by Laeys on 2010-07-30
I had her disconnect the external modem which didn't make a difference, then we searched in the BIOS to try to disable it there but couldn't find anything.

When she went to the recovery menu it spit this out a bunch of times before loading the menu:
serial18250 Too much work for irq17

Then here were the options:
resume normal boot
clean try to make free space
dpkg repair broken packages
grub update grub boot loader
net root drop to root shell prompt with networking
root drop to root shell prompt

---

### Post by robsoles on 2010-07-30
OK, if you can physically detach the modem from the machine then you are not likely to find it in BIOS (even when it is attached) and you may as well leave this modem detached until it will be used.


'grub update grub boot loader' might just happen to fix the problem and **shouldn't** make more problems (but "shouldn't" and "couldn't" are two different things).


If that doesn't happen to fix it for us then may I have the output of
```
 tail /var/log/boot
```and
```
tail /var/log/messages
```after the 'root drop to root shell prompt' option is taken from that menu above.


Either option (from boot choices menu) I have indicated could bomb and if they do then your Mom should wait for harddrive activity to cease and try 'clicking' the power button - if that doesn't shut the machine off within about a minute then she should hold the power button till it forces poweroff.

---

### Post by robsoles on 2010-07-30
> **Laeys said:**
> ...

serial18250 Too much work for irq17

...


Is there an option to disable com ports and parallel port in this machine? In the BIOS under one of the menus?

If there is and your Mom can disable it for us then please tell us if that makes that particular message go away.

---

### Post by Laeys on 2010-07-31
When she tries to run the boot loader update it asks for a login and password.  She tried the the standard admin username and password but it said invalid login.  Am I missing something here?  There is no other username that I am aware of.

I'm still waiting for her to try the other stuff.

---

### Post by robsoles on 2010-08-01
Someone who can 'sudo' should suffice to get that update to run - Is it your Mom's username that you mean by 'standard admin' or do you mean root or ???

Right now I think that disabling the COM ports has a pretty good chance of getting this machine to boot - of course having been wrong plenty of times before makes me unwilling to bet more than about a $1 on it!

---

### Post by Laeys on 2010-08-01
We turned off the parallel port and all of the serial ports.  The too much work message was still there but afterwards my mom was able to launch the grub loader update after selecting resume normal boot(using the same login and password that didn't work before) however it just gave a message saying it can update this this and that and left off at a regular prompt.  I had her enter update-grub but it said permission denied.

The tail /var/log/boot command resulted in:
"nothing has been logged yet"
and tail /var/log/messages gave:
```

Aug  1 14:32:12 ubuntu kernel: [  111.672564] NET: Registered protocol family 17
Aug  1 14:32:14 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Aug  1 14:32:14 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Aug  1 14:32:14 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug  1 14:32:14 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Aug  1 14:32:14 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Aug  1 14:32:17 ubuntu kernel: [  116.505563] NET: Registered protocol family 10
Aug  1 14:32:17 ubuntu kernel: [  116.506543] lo: Disabled Privacy Extensions
Aug  1 18:32:28 ubuntu pulseaudio[8326]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug  1 18:32:28 ubuntu pulseaudio[8326]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
```

I just wanted to let you know I really appreciate your helping out.  My mom is getting frustrated and says she just wants to get a new computer.  Its a 6-8 year old computer so I don't think that's a horrible idea.

---

### Post by robsoles on 2010-08-01
Very welcome, sounds to me like your Mom has been pretty patient with that old clunker and easily deserves a new computer. There are some odd entries (to me at least) in the tail of the messages log but nothing obvious to pursue. '8250' refers to serial communication and disabling COM ports should be enough IMHO.

If the machine boots off LiveCD OK and doesn't flood with that error then there is some chance that it's garbage on the HDD that is causing the problem and just reinstalling may give the computer new legs - your Mom would need to copy all of her personal files she wants to keep to a large enough USB drive using the LiveCD and then start from scratch. Horrible chance is that it's the HDD itself (somehow) though.

I think you should probably be a sweetie and post her a copy of the 10.04 LTS i386 CD. (When is the last time you covered the 1000 miles and just popped in on her? :))

One of the options on the recovery menu (boot with shift key pressed) should include the words 'rebuild packages', or perhaps 'repair' instead of 'rebuild', did your Mom try that?

---

### Post by Laeys on 2010-08-01
I still don't know how to access the old files from the live CD.  It won't seem to let us mount it from the places menu, is there another way to access them?

---

### Post by robsoles on 2010-08-01
Is this a desktop or a laptop? I have the impression it's a desktop.

It would possibly be helpful to know how drives are physically connected to the motherboard - I have a sneaky suspicion that the HDD is on one IDE controller and the CD/DVD ROM is on another one - can your Mom pop the case open and look if the ribbon cables are plugged into separate connectors on the motherboard?

Maybe she could just open the first menu in BIOS (something like 'standard') and list the drives that are listed there for us (depending on her BIOS).

It may be that a new computer with new HDD needs to be acquired and we leave it to faith that the old HDD can be temporarily hooked up to the new machine to get her personal files off it.


Mounting using terminal:

(Not sure 'mkdir' is a legal command when booted off the LiveCD but for purpose of mounting like this it must be. I am not in a position to try right now but here goes.)
```
cd /media
mkdir temp
mount /dev/sda /media/temp

```

at which point, unless your Mom is keen to 'play' in terminal she should try to navigate to the mountpoint using the GUI - hopefully after manually mounting the HDD like that (if it will do it for her) she will be able to get the GUI to mount a USB drive and copy her stuff.

---

