---
title: "Karmic: No Sound"
date: 2009-11-10
forum: General Help
---

### Post by szaemon on 2009-11-10
Hi folks, 

I've been using Karmic on since it was released (Oh so long ago) and as of yet I have no sound. I'm waiting patiently(READ:Idly/Lazily) for my Update manager to Magically surprise me one day and give me Audio.

....Should I keep holding my breath? Is fixing the sound issues on a high priority list somewhere in the Ubuntu Spell Casting Research Labs... Or is it time to fend for myself or starve?

Not very knowledgeable about all the "computery" type stuff yet, so I usually just take what I'm given and say thank you.

I think this is the information I need to start the research project myself(though I'm not to sure):

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 

If someone could just tell me what to do with this...please...
Thanks.
szaemon

---

### Post by hazyumps on 2009-11-10
Try looking on the top right corner of the menu bar...there should be a speaker icon...rightckick...sound prefs...output...and let me know if your card shows up as an option

---

### Post by mastergunner on 2009-11-10
I am having the same problem with no sound. This was a fresh install not upgrade.

---

### Post by szaemon on 2009-11-11
> **hazyumps said:**
> Try looking on the top right corner of the menu bar...there should be a speaker icon...rightckick...sound prefs...output...and let me know if your card shows up as an option

Well I'm not sure if this is my card. I don't know what to look for really.

In the Sound Preferences Box under the tab Hardware, it reads:
Internal Audio Analog Stereo Duplex. 

When I run the sound test from System Testing it reads this as y Sound Device:
Detecting your sound device(s):

0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfda38000 irq 16

Does this tell you anything?

---

### Post by szaemon on 2009-11-11
Ooops! I forgot my manners. Hazyumps, thank you very much for taking an interest in my problem.

---

### Post by szaemon on 2009-11-11
Hey Guys I was looking around in my computer and I noticed this file that called Default Sound Card. I found it in here:

/usr/share/app-install/desktop

So< I opened it up to take a look this is what I saw:

[Desktop Entry]
X-AppInstall-Package=asoundconf-gtk
X-AppInstall-Popcon=321
X-AppInstall-Section=universe

Version=1.0
Encoding=UTF-8
Name=Default Sound Card
Type=Application
Terminal=false
Exec=/usr/bin/asoundconf-gtk
GenericName=asoundconf-gtk
Comment=Allows you to select the default ALSA sound card
Icon=gnome-settings-sound
Categories=GTK;Settings;HardwareSettings;
StartupNotify=true
X-Ubuntu-Gettext-Domain=app-install-data

Can I use this somehow to "select the default ALSA sound card" like it says? Terminal is set to False. If I set it to True would that do something about my sound problems?

Please let me know what you all think.
Thanks,
szaemon

---

### Post by Claus7 on 2009-11-11
Hello ubuntu forum users,

my kindest regards to all of you, since I see that you are ubuntu forum members since 2006!

Now concerning your problem:
what you have to check out is whether your sound card is detected by ubuntu. About that you can try  lspci command.

Also you can select it for your system from System menu (either Preferences or Administration - I'm not in karmic at the moment-). 

Then I would advice you to check my following thread and see if you can make out anything firstly with pulse and secondly without it.
[http://ubuntuforums.org/showthread.php?t=1311599](http://ubuntuforums.org/showthread.php?t=1311599)
There you will be able to find configurations about alsa as well.

If your sound card was working in a previous installation of ubuntu (earlier version) I would suggest you to remove entirely pulse. I did it and my sound is working like a charm.

Regards!

---

### Post by mastergunner on 2009-11-11
> **Claus7 said:**
> Hello ubuntu forum users,

my kindest regards to all of you, since I see that you are ubuntu forum members since 2006!

Now concerning your problem:
what you have to check out is whether your sound card is detected by ubuntu. About that you can try  lspci command.

Also you can select it for your system from System menu (either Preferences or Administration - I'm not in karmic at the moment-). 

Then I would advice you to check my following thread and see if you can make out anything firstly with pulse and secondly without it.
[http://ubuntuforums.org/showthread.php?t=1311599](http://ubuntuforums.org/showthread.php?t=1311599)
There you will be able to find configurations about alsa as well.

If your sound card was working in a previous installation of ubuntu (earlier version) I would suggest you to remove entirely pulse. I did it and my sound is working like a charm.

Regards!

I am using Kubuntu so I am not seeing alot of what you are saying for instructions.

---

### Post by Claus7 on 2009-11-12
Hello,

> **mastergunner said:**
> I am using Kubuntu so I am not seeing alot of what you are saying for instructions.

ehmm, sorry that I didn't notice that. And I cannot tell you much since I do not use kubuntu. Yet, some commands are the same. I do not know if this link will give you some info on how to set your sound options:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Regards!

---

### Post by szaemon on 2009-11-13
> **Claus7 said:**
> Hello ubuntu forum users,

my kindest regards to all of you, since I see that you are ubuntu forum members since 2006!

Now concerning your problem:
what you have to check out is whether your sound card is detected by ubuntu. About that you can try  lspci command.

Also you can select it for your system from System menu (either Preferences or Administration - I'm not in karmic at the moment-). 

Then I would advice you to check my following thread and see if you can make out anything firstly with pulse and secondly without it.
[http://ubuntuforums.org/showthread.php?t=1311599](http://ubuntuforums.org/showthread.php?t=1311599)
There you will be able to find configurations about alsa as well.

If your sound card was working in a previous installation of ubuntu (earlier version) I would suggest you to remove entirely pulse. I did it and my sound is working like a charm.

Regards!

Thanks Claus7 for stepping in and offering help. You say run the lspci command. I did that. Is this my Sound Card?:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

I started my post woth this information from the lspci command, just wasn't sure what to do with it.

I'll check out the Website you mentioned and see what I can see.

As for selecting my card in sound preferences, I am using Karmic, but I don't see any card options under the hardware tab in Sound Preferences. It just reads:

Internal Audio
1 Output/1 Input
Analog Stereo Duplex

I see no way of selecting or unselecting it.

Thanks for any advice you have to offer.

---

### Post by klemes on 2009-11-13
Hey szaemon have a look at my answer in a similar problem like yours in this post:

[http://ubuntuforums.org/showthread.php?p=8307265#post8307265]("http://ubuntuforums.org/showthread.php?p=8307265#post8307265")

---

### Post by szaemon on 2009-11-14
> **klemes said:**
> Hey szaemon have a look at my answer in a similar problem like yours in this post:

[http://ubuntuforums.org/showthread.php?p=8307265#post8307265]("http://ubuntuforums.org/showthread.php?p=8307265#post8307265")

Thanks.

So are you suggesting that I might also try this:

First of all try the command :

Code:

sudo modprobe snd_hda_intel

and then :

Code:

sudo alsa force-reload

If this doesnt work edit your /etc/modprobe.d/alsa-base.conf
and add in the last line :

Code:

options snd-hda-intel model=auto

save and then give in the terminal sudo alsa force-reload.
This will most propably work.It worked for me with the same soundcard.
__________________

---

### Post by szaemon on 2009-11-15
Well I'm not sure if you intended for me to put in those exact codes or not, but I tried them and no dice. Still no sound.
Thanks for trying though.

---

### Post by Claus7 on 2009-11-16
Hello,

so being in front of karmic is easier to give you some better notes on the subject:

first in order to see how many sound cards you have the best is to type:
```
lspci | grep audio
```

I have two and with this command I can see clearly both of them...

So you seem to have at least one card with the specs you give us above.

Secondly, if you go to System -> Preferences you should be able to see the option Default Sound Card.

I do not know whether in the final version this is missing. I have to admit that for now I cannot change anything from there since that option seem not to open any more, yet my sound is rocking! From there, in the alpha days, I was able to choose my default sound device.

Thirdly: Did you check any of my links that I provided you before? 

4th: Could you give us the output of the command:
```
lspci -n
```
with this command in combination to the first you will be able to see whether your sound card is supported by the karmic kernel. 

5th: which was the exact name of the file you opened in /usr/share/app-install/desktop ??

6th: I can no longer help you with pulse audio settings, because I have got rid of pulse, and I saw that my sound is working pretty nicely. 

Regards!

---

### Post by szaemon on 2009-11-19
OK, so when I put in” lspci | grep audio
” just like that, nothing happens. So I tried putting them in sepperately. The result of  “ lspci ”  is below. As for putting in “ grep audio
” on its own...the terminal never stops processing.  I gave it a whole night to finish. 

me@mycomputer:~$ lspci | grep audio

me@mycomputer:~$ lspci

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

01:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)

01:00.2 IDE interface: Intel Corporation Device 108d (rev 03)

01:00.3 Serial controller: Intel Corporation Active Management Technology - SOL (rev 03)

sudo modprobe snd-
01:00.4 IPMI SMIC interface: Intel Corporation 82573E KCS (Active Management) (rev 03)

02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)

02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)

me@mycomputer:~$ grep audio


Then I put in  lspci -n (well, after closing and restarting the terminal that is) and I got this:

me@mycomputer:~$ lspci -n

00:00.0 0600: 8086:2770 (rev 02)

00:02.0 0300: 8086:2772 (rev 02)

00:02.1 0380: 8086:2776 (rev 02)

00:1b.0 0403: 8086:27d8 (rev 01)

00:1c.0 0604: 8086:27d0 (rev 01)

00:1d.0 0c03: 8086:27c8 (rev 01)

00:1d.1 0c03: 8086:27c9 (rev 01)

00:1d.2 0c03: 8086:27ca (rev 01)

00:1d.3 0c03: 8086:27cb (rev 01)

00:1d.7 0c03: 8086:27cc (rev 01)

00:1e.0 0604: 8086:244e (rev e1)

00:1f.0 0601: 8086:27b8 (rev 01)

00:1f.1 0101: 8086:27df (rev 01)

00:1f.2 0101: 8086:27c0 (rev 01)

00:1f.3 0c05: 8086:27da (rev 01)

01:00.0 0200: 8086:108c (rev 03)

01:00.2 0101: 8086:108d (rev 03)

01:00.3 0700: 8086:108f (rev 03)

01:00.4 0c07: 8086:108e (rev 03)

02:00.0 0607: 1180:0476 (rev 82)

02:00.1 0607: 1180:0476 (rev 82)

me@mycomputer:~$ 


As for system>preferences>sound, I have the same situation as you. There is nothing to actually “chose”. I can see the information I posted earlier about the internal input/output analogue stereo, but that's all.

As for your links you provided.Yes I went through them.

 me@mycomputer:~$ alsamixer


AS for those Bars: Line,Mic and Beep were muted. As for PCM and Mic Boos, they do not have the segmented box at the bottom(below the white portion of the bar) which would contain either “00” or ”MM”.  Is that wrong? I can't see if they are muted or not.

Now as for Pulse Audio:  “Applications> Sound&Video>PulseAudio Device Chooser” does not exist. Under  “Applications> Sound&Video>” I have Brasero Disk Burner, Movie Player, rhythm Box and Sound Reccorder. That's all, no Pulse Audio Device Chooser”. So I don't know what's up with that. But I have no choice but to take another road...

So then I tried this command:

me@mycomputer:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]

  Subdevices: 0/1

  Subdevice #0: subdevice #0


I suppose that's my Intel Sound Card/Chipset...whatever...still don't really understand the difference between  soundcard and chipset device...

So then on to step two:

(I'm not sure what language any of this stuff is in, though it looks like it might have its origins in English or Latin...)

me@mycomputer:~$ lspci -v

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, fast devsel, latency 0

	Capabilities: <access denied>

	Kernel driver in use: agpgart-intel

	Kernel modules: intel-agp



00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

	Subsystem: NEC Corporation Device 8315

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at fda80000 (32-bit, non-prefetchable) [size=512K]

	I/O ports at ac00 [size=8]

	Memory at e0000000 (32-bit, prefetchable) [size=256M]

	Memory at fda40000 (32-bit, non-prefetchable) [size=256K]

	Capabilities: <access denied>

	Kernel driver in use: i915

	Kernel modules: i915

00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

	Subsystem: NEC Corporation Device 8315

	Flags: bus master, fast devsel, latency 0

	Memory at fd980000 (32-bit, non-prefetchable) [size=512K]

	Capabilities: <access denied>



00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

	Subsystem: NEC Corporation Device 830a

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at fda38000 (64-bit, non-prefetchable) [size=16K]

	Capabilities: <access denied>

	Kernel driver in use: HDA Intel

	Kernel modules: snd-hda-intel



00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

	I/O behind bridge: 0000b000-0000cfff

	Memory behind bridge: fdb00000-fdbfffff

	Capabilities: <access denied>

	Kernel driver in use: pcieport-driver

	Kernel modules: shpchp



00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, medium devsel, latency 0, IRQ 23

	I/O ports at a880 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, medium devsel, latency 0, IRQ 19

	I/O ports at a800 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, medium devsel, latency 0, IRQ 18

	I/O ports at a480 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, medium devsel, latency 0, IRQ 16

	I/O ports at a400 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, medium devsel, latency 0, IRQ 23

	Memory at fda37c00 (32-bit, non-prefetchable) [size=1K]

	Capabilities: <access denied>

	Kernel driver in use: ehci_hcd



00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=02, subordinate=07, sec-latency=32

	I/O behind bridge: 0000d000-0000efff

	Memory behind bridge: fdc00000-febfffff

	Prefetchable memory behind bridge: 00000000f9000000-00000000fcffffff

	Capabilities: <access denied>



00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, medium devsel, latency 0

	Capabilities: <access denied>

	Kernel modules: iTCO_wdt, intel-rng



00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, medium devsel, latency 0, IRQ 18

	I/O ports at 01f0 [size=8]

	I/O ports at 03f4 [size=1]

	I/O ports at 0170 [size=8]

	I/O ports at 0374 [size=1]

	I/O ports at ffa0 [size=16]

	Kernel driver in use: ata_piix



00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19

	I/O ports at a080 [size=8]

	I/O ports at a000 [size=4]

	I/O ports at 9c00 [size=8]

	I/O ports at 9880 [size=4]

	I/O ports at 9800 [size=16]

	Capabilities: <access denied>

	Kernel driver in use: ata_piix



00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

	Subsystem: NEC Corporation Device 831d

	Flags: medium devsel, IRQ 10

	I/O ports at 0400 [size=32]

	Kernel modules: i2c-i801



01:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)

	Subsystem: NEC Corporation Device 8322

	Flags: bus master, fast devsel, latency 0, IRQ 25

	Memory at fdbe0000 (32-bit, non-prefetchable) [size=128K]

	Memory at fdb00000 (32-bit, non-prefetchable) [size=512K]

	I/O ports at cc00 [size=32]

	Capabilities: <access denied>

	Kernel driver in use: e1000e

	Kernel modules: e1000e



01:00.2 IDE interface: Intel Corporation Device 108d (rev 03) (prog-if 85 [Master SecO PriO])

	Subsystem: NEC Corporation Device 0000

	Flags: fast devsel, IRQ 17

	I/O ports at c880 [size=8]

	I/O ports at c800 [size=4]

	I/O ports at c480 [size=8]

	I/O ports at c400 [size=4]

	I/O ports at c080 [size=16]

	Capabilities: <access denied>



01:00.3 Serial controller: Intel Corporation Active Management Technology - SOL (rev 03) (prog-if 02)

	Subsystem: NEC Corporation Device 0000

	Flags: bus master, fast devsel, latency 0, IRQ 18

	I/O ports at c000 [size=8]

	Memory at fdbdb000 (32-bit, non-prefetchable) [size=4K]

	Capabilities: <access denied>

	Kernel driver in use: serial



01:00.4 IPMI SMIC interface: Intel Corporation 82573E KCS (Active Management) (rev 03) (prog-if 01)

	Subsystem: NEC Corporation Device 0000

	Flags: fast devsel, IRQ 19

	Memory at fdbda000 (32-bit, non-prefetchable) [size=4K]

	I/O ports at bc00 [size=4]

	Capabilities: <access denied>



02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, medium devsel, latency 168, IRQ 16

	Memory at fdc00000 (32-bit, non-prefetchable) [size=4K]

	Bus: primary=02, secondary=03, subordinate=03, sec-latency=176

	Memory window 0: 40000000-43fff000 (prefetchable)

	Memory window 1: 44000000-47fff000

	I/O window 0: 0000d000-0000d0ff

	I/O window 1: 0000d400-0000d4ff

	16-bit legacy interface ports at 0001

	Kernel driver in use: yenta_cardbus

	Kernel modules: yenta_socket



02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)

	Subsystem: NEC Corporation Device 831d

	Flags: bus master, medium devsel, latency 168, IRQ 17

	Memory at fdc01000 (32-bit, non-prefetchable) [size=4K]

	Bus: primary=02, secondary=04, subordinate=07, sec-latency=176

	Memory window 0: 48000000-4bfff000 (prefetchable)

	Memory window 1: 4c000000-4ffff000

	I/O window 0: 0000d800-0000d8ff

	I/O window 1: 0000dc00-0000dcff

	16-bit legacy interface ports at 0001

	Kernel driver in use: yenta_cardbus

	Kernel modules: yenta_socket



I've read this but, if my answer lies somewhere within it, I wouldn't know how to see it... 

(3)Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).

Well, I went there but didn't see any drop down box. Then I looked through the Parent Directory Link and the alsa-lib/ link....but again, I'm afraid I don't really know what I'm looking for or what I'm looking at.

...I'll keep working on it. I just wanted to post my current situation in case you or anyone else wants to offer me more guidance.

Thanks again!

---

### Post by Claus7 on 2009-11-19
Hello,

> OK, so when I put in&#8221; lspci | grep audio
&#8221; just like that, nothing happens.

This is normal as in your audio devices there is no word as audio.

>  So I tried putting them in sepperately. The result of  &#8220; lspci &#8221;  is below. 

This command will give you the output of all your pci devices, meaning all the devices that they are attached to your motherboard via a pci slot (including your sound card)

> As for putting in &#8220; grep audio
&#8221; on its own...the terminal never stops processing.  I gave it a whole night to finish. 

And it wasn't supposed to finish as grep takes from an input every single line and outputs the lines that include the string after the word grep.


> me@mycomputer:~$ lspci

*00:1b.0* Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Then I put in  lspci -n (well, after closing and restarting the terminal that is) and I got this:

me@mycomputer:~$ lspci -n

*00:1b.0* 0403: 8086:27d8 (rev 01)

These are the specs of your sound card.

> As for system>preferences>sound, I have the same situation as you. There is nothing to actually &#8220;chose&#8221;. I can see the information I posted earlier about the internal input/output analogue stereo, but that's all.

You do not, as it seems that you have only one sound device.

> As for your links you provided.Yes I went through them.

 me@mycomputer:~$ alsamixer


AS for those Bars: Line,Mic and Beep were muted. As for PCM and Mic Boos, they do not have the segmented box at the bottom(below the white portion of the bar) which would contain either &#8220;00&#8221; or &#8221;MM&#8221;.  Is that wrong? I can't see if they are muted or not.

I suppose that they should show something there...
Can you see if by typing this command you can recognize in the top left corner of the window that appears your sound card? I mean: does alsa recognizes your sound card? 

> Now as for Pulse Audio:  &#8220;Applications> Sound&Video>PulseAudio Device Chooser&#8221; does not exist. Under  &#8220;Applications> Sound&Video>&#8221; I have Brasero Disk Burner, Movie Player, rhythm Box and Sound Reccorder. That's all, no Pulse Audio Device Chooser&#8221;. So I don't know what's up with that. 

Go to synaptic package manager and install the package with that name: *padevchooser*

Then you will be able to see the option I'm describing you.


> But I have no choice but to take another road...

So then I tried this command:

me@mycomputer:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]

  Subdevices: 0/1

  Subdevice #0: subdevice #0

Alsa seems to understand your sound device...


> I suppose that's my Intel Sound Card/Chipset...whatever...still don't really understand the difference between  soundcard and chipset device...

[I]A chipset or chip set refers to a group of integrated circuits, or chips, that are designed to work together. They are usually marketed as a single product.

In computing, the term chipset is commonly used to refer to a set of specialized chips on a computer's motherboard or an expansion card.

The manufacturer of a chipset often is independent from the manufacturer of the motherboard. Current manufacturers of chipsets for PC-compatible motherboards include NVIDIA, AMD, VIA Technologies, SiS, Intel and Broadcom.[/I] ...source wikipedia
Hope it gives some insight...

> So then on to step two:

(I'm not sure what language any of this stuff is in, though it looks like it might have its origins in English or Latin...)

me@mycomputer:~$ lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

	Subsystem: NEC Corporation Device 830a

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at fda38000 (64-bit, non-prefetchable) [size=16K]

	Capabilities: <access denied>

	Kernel driver in use: HDA Intel

	Kernel modules: snd-hda-intel


I've read this but, if my answer lies somewhere within it, I wouldn't know how to see it... 

by invoking the command lspci with the -v option you do exactly as before, yet the results are more verbose, that means that you get more details as output. If you type that command as root you will get even more.

> (3)Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).

Well, I went there but didn't see any drop down box. Then I looked through the Parent Directory Link and the alsa-lib/ link....but again, I'm afraid I don't really know what I'm looking for or what I'm looking at.

From here:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

I suppose that you sound card is supported...

> ...I'll keep working on it. I just wanted to post my current situation in case you or anyone else wants to offer me more guidance.

Some things even being trivial, need some effort in order to be solved. Check also the pulse audio options in case you make out something from there. Also you could reinstall everything that has to do with alsa packages, yet I do not think that this might solve your problem. Yet, you do not loose much in order to try. Also in alsamixer check out if master bar (the first one) is muted or not. Is this bar filled or is it empty? 

And just a final question: Were you able to have sound from a previous ubuntu version?

> Thanks again!


You are welcome!
Hope I gave you some insight..

Regards!

---

### Post by Claus7 on 2009-11-19
Hello,

searching a little I came across this post:
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8296711&postcount=10](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8296711&postcount=10)

it might be helpful.

Regards!

---

### Post by szaemon on 2009-11-19
Let me answer your last question first as that may be quite pertinent to my problem. You asked about sound with earlier versions of Ubuntu. On this system I was not able to even install any earlier versions of Ubuntu due to some graphics incompatibility issues with the 
Intel 945G Express Chipset.

I did however have fully functioning sound with the Japanese Version of Windows XP Pro the system originally came with. 

>Can you see if by typing this command you can recognize in the top left corner of the window that appears your sound card? I mean: does alsa recognizes your sound card?

I believe this means it recognizes my HDA Intel Card, but with nothing more descriptive than HDA Intel, perhaps this is just some generic recognition. I don't know.


Card:HDAIntel                                                          
Chip:RealtekALC262                                                     View:[Playback]CaptureAll                                              Item:Master[dBgain=0.00]                                               


OK, so I guess alsa is recognizing my sound card. If these are the spec for my sound card:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

00:1b.0 0403: 8086:27d8 (rev 01)

Then following the link you gave me, whatever my sound card needs would be listed in IHC7 link.

It reads

"Introduction for HDA Intel soundcard

There are two ways of getting Linux drivers to work, you can either compile them into the kernel or build them separately as modules. Read the Kernel-HOWTO for details of how to compile a kernel.

**You must turn on the sound support soundcore module.** This is in the kernel. Look in the sound drivers directory and it should be the first option. Most people enable the module setting. That way you can load and unload the module manually if you have multiple soundcards/&#8203;devices or if you intend to debug or use cutting edge software which may cause your drivers to halt sometimes. Of course it also means you have more control of your system.

Most modern distros come with soundcore compiled as a module. You can check this in numerous ways. The easiest way is to type:

       modinfo soundcore

[COLOR="Red"]If this command returns that you have this module[/COLOR], then you don't need to recompile your kernel. " 

I ran the code mentioned:
me@mycomputer:~$ modinfo soundcore
filename:       /lib/modules/2.6.31-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
[COLOR="Red"]description:    Core sound module[/COLOR]
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-14-generic SMP mod_unload modversions 586 
me@mycomputer:~$ 

So I guess I do have the module, so I don't need to recompile the kernel. But I do need to turn on the sound support soundcore module, which is in the kernel, in the sound drivers directory.

Where? Do I need to be a root user to access this section? I don't quite know where to look for the kernel or the sound drivers directory.

As for this information:

00:1b.0 0403: 8086:27d8 (rev 01)

I'm not sure what it means or how I can use it to help me.
What does it identify about my sound card?

As for Pulse Audio, I had already followed the instructions on how to remove it. Now I've just reinstalled it I put in the but the padevchooser, in doing so Synaptic told me it was removing a program called "esound" or some such thing.

So I opened the Manager.

Now in the Sample Cache Tab, I hear no sounds.

under the Modules Tab, everything is empty except Module alsa-card. It has a long line of stuff, but it won't let me copy and paste it...
The properties for the Module alsa-card does say "Autoloaded: NO". That may be important.

Last thing I&m going to try before I get to sleep tonight is the command:
killall pulseaudio

I think that's suppose to resart pulse audio or something.

Thanks again for taking an interest in my problem.

---

### Post by Claus7 on 2009-11-19
Hello *szaemon*,

I have faced similar problems as yours, so I can understand exactly your situation and how it feels. Yet, when you are able to fix it, you will see that you have gained something and that your life has become much more easier. 

From what you are writing I do understand that you do many things simultaneously which might have conflicts as well. The bad thing is that you can not know beforehand what you are doing, because some situations are more like trial and error.

Concerning your problem, typing the 
```
modinfo soundcore
```
command I get exactly the same output as yours.

Before anything else, I would suggest you to see the last link I provided you in my previous post, as it has the same problem as yours. And there are many solutions to this post that might apply to your situation.

Also, if it is convenient, is it possible to see snapshots from your alsamixer command? The thing that some options are missing is a little bit weird...

I hope that I can give you some insight on the issue and not perplex you.
I hope also that you will be able to solve your problems.

Regards!

---

### Post by Paul D on 2009-11-19
I was having a similar issue as well. In a post somewhere (I think) I installed a Gnome alsa Mixer deal. After selecting the GNOME ALSA mixer, a window poped up that allowed me to ckeck my Audigy analog output jack. I don't know if that would be similar for you or not. Just trying to help.

---

### Post by exploitations on 2009-11-19
I'm not sure if this'll help or not, but in your sound preferences, is the headphone option selected? If it is, its most likely sending audio through the headphone jack on your tower/laptop (what ever you're using)

I had the same problem, until I played around with the settings

---

### Post by szaemon on 2009-11-20
Here&s the screenshot of my alsamixer and this result of sudo alsa force-reload looks strange. Are those warnings normal? 

me@mycomputer:~$ sudo alsa force-reload

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/me/.gvfs

      Output information may be incomplete.

Terminating processes: 2300lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/me/.gvfs

      Output information may be incomplete.

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/me/.gvfs

      Output information may be incomplete.

.

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/me/.gvfs

      Output information may be incomplete.

Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-intel snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.

Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-intel snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.


Thanks Claus, for you words of encouragement.
...I'll keep at it.

---

### Post by szaemon on 2009-11-20
> **exploitations said:**
> I'm not sure if this'll help or not, but in your sound preferences, is the headphone option selected? If it is, its most likely sending audio through the headphone jack on your tower/laptop (what ever you're using)

I had the same problem, until I played around with the settings

Thanks for the concern exploitations, I can use all the help I can get with this. Here's what my sound preferences are set to(see the screen shot) and the only other options in that drop down box would change Duplex to Input or change it to output.

Does that look right to you?

---

### Post by szaemon on 2009-11-20
> **Paul D said:**
> I was having a similar issue as well. In a post somewhere (I think) I installed a Gnome alsa Mixer deal. After selecting the GNOME ALSA mixer, a window poped up that allowed me to ckeck my Audigy analog output jack. I don't know if that would be similar for you or not. Just trying to help.

Thanks Paul. I'll try that one too. I'm doing all the options that come up and if I break the machine, I'll reistall and start trying them again.
Wish me luck!

---

### Post by szaemon on 2009-11-20
Oh, almost forgot, Cluas, thanks for that link. They do indeed have a lot of possible fixes for this problem. That exact one from mich that you posted couldn't do the trick for me (possibly because I don't have a sound setting with "surround" in it), but I'm checking out all the options presented.

---

### Post by Claus7 on 2009-11-20
Hello *szaemon*,

you are very kind and you do not have to say thanks. My pleasure if I can give you some insight on the subject.

Now concerning your issues:

> Here&s the screenshot of my alsamixer
As you have pointed out before your PCM bar does not have underneath any option of muting, yet in every computer I tried I was able to see that option. I do not know for sure, whether this is a problem or not though...

> and this result of sudo alsa force-reload looks strange. Are those warnings normal? 

me@mycomputer:~$ sudo alsa force-reload

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/me/.gvfs

Output information may be incomplete.

Terminating processes: 2300lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/me/.gvfs

Output information may be incomplete.

No, I do not think that there warnings are normal. I do the same command to my pc, and I do not get this warnings. The command works normally without warnings.

Searching a little bit, I saw this bug in ubuntu Karmic, so it is not precluded that this might be your case.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/445585](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/445585)

> ...If it is, its most likely sending audio through the headphone jack on your tower/laptop (what ever you're using)...

Here if I understand correctly, you could plug some headphones and see if you get sound from there, so as to eliminate this issue.

Hope you will solve your problem soon,
Regards!

---

### Post by Claus7 on 2009-11-20
Hello,

from what I can make out, this is probably a bug, yet this seems to be the "easy" solution. While being at the forums, I remembered that I had taken a look on this guide:
[http://ubuntuforums.org/showpost.php?p=1191847&postcount=1](http://ubuntuforums.org/showpost.php?p=1191847&postcount=1)

some time ago, and it was really comprehensible.

I post it here for others to find it useful as well. 

Regards!

---

### Post by szaemon on 2009-11-21
> **exploitations said:**
> I'm not sure if this'll help or not, but in your sound preferences, is the headphone option selected? If it is, its most likely sending audio through the headphone jack on your tower/laptop (what ever you're using)

I had the same problem, until I played around with the settings

Exploitations! That is it. At first I was at a loss as to test your idea, because I don't yet see how to set my sound to come out of headphones. However Claus came up with the brilliantly obvious idea of just plugging in a set of headphones to check it out. Sometimes when it comes to computers, I think my brain is eternally in the crapper. I just get lost looking at a computer.  Damn! It's so frustrating being this ignorant of such a vital tool.

Thank you All(and Yes I do need to say Thank You for all the help I get online, I would be lost without the assistance of the online community) So now I know what problem I'm suffering from, next is finding the fix which is probably already out there somewhere.

---

### Post by szaemon on 2009-11-21
Hey Guys, It seems like it should be a simple fix, but in my sound preferences, there doesn&t seem to be any option for chosing headphones or anything else.
Should I be trying to do this through the Terminal?
Would it make any difference if I were logged in as Root?

---

### Post by Claus7 on 2009-11-21
Hello,

what about this one?
[http://ubuntuforums.org/showthread.php?t=384512](http://ubuntuforums.org/showthread.php?t=384512)

Glad that we are narrowing the problem!

Regards!

---

### Post by szaemon on 2009-11-21
> **Claus7 said:**
> Hello,

what about this one?
[http://ubuntuforums.org/showthread.php?t=384512](http://ubuntuforums.org/showthread.php?t=384512)

Glad that we are narrowing the problem!

Regards!

Thanks Claus, that might work...I'll have to try it when I get Gnome back...In frustration I uninstalled everything invovled with alsa and then installed everything I could find with alsa in it...more stuff than I had originally uninstalled. When I rebooted...I got a black screen and a terminal. Needless to say I'm lost at that point. I&m surfing on the live CD right now hoping I don&t have to reinstall the whole OS... Any advice?

---

### Post by Claus7 on 2009-11-21
Hello,

this is not the sound problem: this is shaping as to be the 1000 myriad bad things (1000 &#956;&#973;&#961;&#953;&#945; &#972;&#963;&#953;&#945;...).

Okkk. Now we have a video problem. I cannot think about anything related with video issues while tampering audio. Did you mess with something about video in synaptic as well and not only with alsa?

I would advice you to do a clean install and try the latest post I give you. It would be very difficult to start all over, since you do not provide any errors as well... Now that you narrowed down your problem I think that it will be much easier.

Hope you good luck,
Regards!

---

### Post by szaemon on 2009-11-21
Agreed. I think I broke my system. I just did a fresh install .... but my mouse didn't load in properly. Grrr.... I posted that problem in a new thread. Thanks for all the help you've given. I think that last link might do it. Once I get back to having "just" the sound problem, I'll try it out...

---

### Post by szaemon on 2009-11-22
OK, I've clawed my back up to ground zero. I'm back where I was with the working system minus sound. I tried the fix in that last link referring to opening the alsa file and putting in those 2 lines of code:

Go to terminal and type:
Quote:
sudo gedit /etc/modprobe.d/alsa-base
In that file at the end copy and paste this:

Quote:
options snd-card-0 enable=1 index=0 model=basic
options snd-hda-intel enable=1 index=0 model=basic
Save!

If still doesn't work, run gnome-volume-control and go to Switches tab. Now try to check/uncheck Speaker and Headphones.

...but no go. Sound from the headphone jack is Ultra Quiet and I can't change it.

I guess I'll go back to the beginning and start over with the fixes I've already gone through.

---

### Post by Claus7 on 2009-11-22
Hello *szaemon*,

I'm really sorry hearing that you weren't able to solve your problem following the last link. Other than that I'm afraid I cannot help you anymore.

Either you have to check now, with better knowledge all the steps you took before or to submit a bug in ubuntu launchpad.

There were also a couple of threads:
[http://www.google.gr/search?hl=en&client=opera&rls=en&hs=gWL&q=sound+only+on+headphones+ubuntu&btnG=Search&aq=f&oq=](http://www.google.gr/search?hl=en&client=opera&rls=en&hs=gWL&q=sound+only+on+headphones+ubuntu&btnG=Search&aq=f&oq=)

that they were related to your issue. It seems to me that this is not a trivial problem. Maybe, using an older version of ubuntu might have done the trick, yet I see people having this issue for a long time.

I hope that some of all these things might solve your problem once and for all.
I would also propose you to buy one other card, cheap and good and test it, since this gives you so much headaches. 

I really cannot think anything else. Maybe someone else might be able to give you a hand.

I was glad to give you any advice that I was able to give.

Good luck,
Regards!

---

### Post by szaemon on 2009-11-22
Well Claus, your help has not been in vain. A large part of finding out what WILL fix a problem is first discovering what WILL NOT. You have taken me through quite a few possibilities that I would not have discovered without your help and I have learned that mine is not an isolated case. I will keep searching and, with an issue this big, someone is bound to find a permanent solution.

If you see my posts around feel free to drop in your with your ideas and advice. I am still very much a newbie and need to many many things about running a computer.

Thanks again for all your inout.
szaemon

---

### Post by jmoraleda on 2009-11-23
I have a PCI Turtle Beach Riviera card (CMI8738). After upgrading to karmic I had no sound in spite of the fact that the card was recognized correctly by pulse and nothing was muted in the sound preferences.

'alsamixer' returned: "snd_ctl_open failed for default: No such device". However 'alsamixer -c 0' opened alsamixer. (My card was number 0 as shown by 'aplay -l')

The main output channel <IEC 958 O> was muted. I unmuted it and everything worked like a charm. I muted all the other channels because they don't seem to do anything. I think pulse controls those at a higher lever.

---

### Post by Claus7 on 2009-11-23
Hello,

> **szaemon said:**
> Well Claus, your help has not been in vain. A large part of finding out what WILL fix a problem is first discovering what WILL NOT. You have taken me through quite a few possibilities that I would not have discovered without your help and I have learned that mine is not an isolated case. I will keep searching and, with an issue this big, someone is bound to find a permanent solution.

If you see my posts around feel free to drop in your with your ideas and advice. I am still very much a newbie and need to many many things about running a computer.

Thanks again for all your inout.
szaemon

I have been in your shoes *szaemon*. I do know how it feels to have a system down and how to have it up as well. I was very glad to come a give a hand and I will be even more if you are able to solve your problem. *jmoraleda*'s solution seems that might help you as well. 

You are very kind. Also from the process I learn as well this weird, hard, exciting, full of surprises, anger, frustration, yet rewarding world of ubuntu. 

Since you are fighting so much, don't forget to come back and post the solution to your problem.

My kindest regards to the ubuntu registered user of the last quarter of 2006!

---

### Post by szaemon on 2009-12-15
Well, I'm back. I wish I was posting a solution, but I'm still suffering from this "Dumb" problem. Just checking in to see if any answer has come up...

---

### Post by szaemon on 2010-01-03
Still looking to end my system's vow of silence. If anyone has a clue what I can try next, please post it.
Thanks,
szaemon

---

### Post by Marrkk on 2010-01-04
no real good answers from me i'm afraid.. but sounds like another pulseaudio problem to me.
i cant use Ubuntu as the sound is broken, 
my suggestion is a really crap one :(
dont use pulseaudio. 
sound problems made me not use Ubuntu 9.10 karmic.
i use skype alot and i need a Linux with a good audio system.

Mepis 8  is lovely, but a bit old looking, KDE 3.5, but everything is as stable as you can get. nice.
i'm using Xubuntu with a carefully installed and tweaked KDE 4.3.
Kubuntu 9.10 may be better,it does'nt suffer pulseaudio problems
hope you find your Linux :)

---

### Post by szaemon on 2010-01-07
> **Marrkk said:**
> no real good answers from me i'm afraid.. but sounds like another pulseaudio problem to me.
i cant use Ubuntu as the sound is broken, 
my suggestion is a really crap one :(
dont use pulseaudio. 
sound problems made me not use Ubuntu 9.10 karmic.
i use skype alot and i need a Linux with a good audio system.

Mepis 8  is lovely, but a bit old looking, KDE 3.5, but everything is as stable as you can get. nice.
i'm using Xubuntu with a carefully installed and tweaked KDE 4.3.
Kubuntu 9.10 may be better,it does'nt suffer pulseaudio problems
hope you find your Linux :)

Thanks Mepis for your advice. I'm still desperate here, so I'll give that a shot. Don't use Pulseaudio. OK, so is removing Pulseaudio as simple as it looks? Just open Synaptic and check the remove boxes? Should I replace Pulseaudio with something or just remove it?

You know, I've never really tried another Distro of Linux. Perhaps others don't have this audio trouble...Is there another one you recommend that's as user friendly as Ubuntu?

---

### Post by anselm on 2010-01-07
There is a thread having instructions how to remove pulse audio and use alsa or ossl. I'll see if I can find it.

---

### Post by Claus7 on 2010-01-12
Hello,

About removing pulse from your box this:
[http://ubuntuforums.org/showpost.php?p=8266465&postcount=5](http://ubuntuforums.org/showpost.php?p=8266465&postcount=5)

might be what you are looking for. I had sent you this link before, yet with all the things you were trying you might have missed it.

Regards!

---

### Post by szaemon on 2010-01-14
> **Claus7 said:**
> Hello,

About removing pulse from your box this:
[http://ubuntuforums.org/showpost.php?p=8266465&postcount=5](http://ubuntuforums.org/showpost.php?p=8266465&postcount=5)

might be what you are looking for. I had sent you this link before, yet with all the things you were trying you might have missed it.

Regards!

Hi Claus, Thanks for checking back with me. As for removing Pulse through that link. I did it and now have no sound icon on the bar at the top of the screen. I think I tried that one before, not sure though. I adjust the sound options through alsamixer and set every bar to 00 at its base and 100 for its setting.
...Still no sound....hmmm...

Hi Anselm. As you can see, I've tried just about everything possible to fix this sound problem. I'm not sure there is anything that can be done for it, but if you have any ideas. Please share them. I have 1 computer in this office and having no sound option has limited the way I do business here.
Thanks for any help you can offer. 

szaemon

---

### Post by Claus7 on 2010-01-14
Hello,

I'm not in my pc right now, yet I think that in mine I do not have a sound icon in the panel either. I would suggest you to buy one external sound card (a cheap one) and be able to do your work. It's a pity not being able to have sound...

Regards!

---

### Post by p.suierveld on 2010-01-14
[QUOTE=Claus7;8652065]Hello,

About removing pulse from your box this:
[http://ubuntuforums.org/showpost.php?p=8266465&postcount=5](http://ubuntuforums.org/showpost.php?p=8266465&postcount=5)

might be what you are looking for. I had sent you this link before, yet with all the things you were trying you might have missed it.

Regards![/QUOT

tried this and many other things, didn't solve a thing for me. But.. found a very nice quick fix for now to wait for 10.4. :P took out me pci audiocart and use my ac96 cart wit no problems. for all desperate people out there :popcorn: regards Pete

---

### Post by szaemon on 2010-01-18
> **p.suierveld said:**
> .. found a very nice quick fix for now to wait for 10.4. :P took out me pci audiocart and use my ac96 cart wit no problems. for all desperate people out there :popcorn: regards Pete

Hi p.suierveld,

Thanks for offering help. Could you elaborate on what you just said please?
What is a pci audiocart? How do I take it out? And where do I get the ac96 cart to replace it with?
Thanks.

---

### Post by garvinrick4 on 2010-01-18
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][SIZE=4]**Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)**[/SIZE]
*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ rm -r ~/.pulse ~/.asound* [/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo rm /etc/asound.conf[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#ff0000]**Warning:**[/COLOR][COLOR=#ff0000] As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Don't worry if some of these files did not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio[/SIZE][/FONT][/COLOR] [[COLOR=#444444][FONT=Verdana, Arial, Tahoma][SIZE=2]_3_[/SIZE][/FONT][/COLOR]]("https://bugs.launchpad.net/bugs/192888")[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]. Ensure the evil "libflashsupport" library is [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]**not**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2] installed: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:[/COLOR][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ pulseaudio & pavucontrol[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ alsamixer [COLOR=#0000ff]-Dhw[/COLOR][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR]

7. Continue to **Part B** if you are running Hardy Heron (8.04), or **Part C** if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect![/SIZE][/FONT][/COLOR]
 

                                     NOW REBOOT TO TAKE EFFECT.

---

### Post by damilaredavids on 2010-01-19
> **szaemon said:**
> Thanks.

So are you suggesting that I might also try this:

First of all try the command :

Code:

sudo modprobe snd_hda_intel

and then :

Code:

sudo alsa force-reload

If this doesnt work edit your /etc/modprobe.d/alsa-base.conf
and add in the last line :

Code:

options snd-hda-intel model=auto

save and then give in the terminal sudo alsa force-reload.
This will most propably work.It worked for me with the same soundcard.
__________________

  This is my output for the first command  dare@dare-desktop:~$ sudo modprobe snd_hda_intel [sudo] password for dare:  WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.  what do i do pls? i am desperate...

---

### Post by Claus7 on 2010-01-19
Hello,

> **damilaredavids said:**
> This is my output for the first command  dare@dare-desktop:~$ sudo modprobe snd_hda_intel [sudo] password for dare:  WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.  what do i do pls? i am desperate...

I have seen that you have made multiple post for your issue. Really, with so little data you provide is impossible to give some help. Also, I do not know if is appropriate to post in a thread without at least giving the necessary data that show that your problem is the same or at least similar to that of the creator of the tread. Nevertheless, in this thread there are various posts that if you follow them step by step you will get a better knowledge on the audio configuration of your system.

Just try not to mess things up by trying multiple things together. Unfortunately, you should reinstall or revert back your system, before you try a new solution. For a starting step it would be nice to know your audio device...

Regards!

---

### Post by szaemon on 2010-01-20
garvinrick4  	

Re: Karmic: No Sound
Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)
All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration...

Thanks garvninrick. I followed your instructions for the proper installation of Pulse Audio. Unfortunately, after the installation it says it's working just fine...but I still get no sound.

Thanks Anyway...

I wonder if anyone else with my computer is using Ubuntu..Or any form of Linux. It seems odd that this problem would exist for so long with no fix or work around being discovered. I can't be the only one suffering...

---

### Post by szaemon on 2010-02-11
Still no sound in Karmic. Are sound issues still a problem or am I the only one left suffering?

---

### Post by Swagman on 2010-02-11
> **szaemon said:**
> Still no sound in Karmic. Are sound issues still a problem or am I the only one left suffering?

Mate.. Your special !

(I couldn't think of a better Politically Correct way of saying "It's only you"!!)

I've installed Karmic on loads of desktops & laptops and even three EeePc 701 netbooks. No sound problems on any of them.

I'll have a gander at my sound settings to see if anything is obvious.  You might have been not able to see the trees for the forest.

---

### Post by Swagman on 2010-02-11
Ok.. Lets think "out of the Box"

Your sound has been detected as internal... I assume that means onboard audio.

Lets start at the beginning.....

Reboot and go into **BIOS** and make sure that Onboard Audio is enabled.

---

### Post by szaemon on 2010-03-02
Hey Swagman sorry for the late response. I appreciate our offer to assist. I put up my last post and didn't check back. I have just kinda accepted being Deaf and Dumb.

I'll check through my Bios and see if Onboard is enabled then post back.
Thanks for taking the time!

---

### Post by szaemon on 2010-03-02
Well I checked the BIOS Utility. Nothing in there says Onboard. The only thing I find that talks about sound is under Advanced Chipset, it's called Audio Controler. It was enabled, but I disabled it just to see if it made a change... no change.

Can I provide you any more information about my system to help you help me?

Again, thanks for stepping up with the offer of help.

Also, I was wondering if downloading and burning another Live DVD might help. With all the updates to Karmic now, a fresh install of the latest version my do the trick.
What do you think?

---

### Post by jweaver28 on 2010-03-02
Just posting Szaemon to say I too am deaf and dumb. I've posted on other threads (created by yet more people waiting for sound in Karmic) and have gotten no replies. Probably telling you that you're not alone doesn't help, but I'm hoping that someone will pay attention....

---

### Post by szaemon on 2010-03-02
Hey jweaver thanks for dropping in. Actually telling me I'm not alone might help. Do we have the same system? Or some similar hardware? Perhaps we can find a common point of incompatibility with Karmic.

---

### Post by szaemon on 2010-04-21
Hey folks, I must be holding the record now for Patience and Hope (or Laziness and Indifference) I've been using Karmic now since...I don't know. When was it released? Well, since then. And never had any sound, though I've tried a plethora of fixes. I'm just checking in to see if anything new has been developed which might help me with this trouble. 

...Perhaps my answer will come with the next release...hmmm...

Anyway, if anyone wants let me know I'm not alone in my suffering, please drop me a note.
Thanks.

---

### Post by szaemon on 2010-04-21
Well I am rather disheartened to see the results of the Beta Version of Ubuntu 10. I have just tried it and got the same results. Everything seems to say that sound is working, but I get no sound.

If Microsoft ever worries about keeping people from switching to Ubuntu, they should keep my computer in mind. A system with no sound might be enough to deter a lot of people.

---

### Post by lidex on 2010-04-21
szaemon:
Have you worked through this page for karmic:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by szaemon on 2010-04-23
Thanks for the interest in my struggles lidex. I'm not sure if I used the Code Tags correctly(first time) As for the make and model of my computer:

It is a refurbished NEC Mate bought from a computer store in Japan named Softmap. When they refurbished it I think it got a knew Model number. The sticker on the front say MY30V/FE-1 on the back it reads MY30VFEE1. I'm not sure what other information you might need to assist me. I'm happy to tell you, but please instruct me how to find that information in my computer. I have no paperwork on the machine. 


me@mycomputer:~$ uname -a

```
Linux mycomputer 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

```

me@mycomputer:~$ aplay -l

```
aplay: device_list:223: no soundcards found...

```

me@mycomputer:~$ cat /proc/asound/version

```
cat: /proc/asound/version: No such file or directory

```

me@mycomputer:~$ head -n 1 /proc/asound/card*/codec#*

```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

I'll check through that page on the link you posted and post back any result from there.
Thanks Again.

---

### Post by szaemon on 2010-04-23
Well, I tried out the stuff on that page, but it led me nowhere.

---

### Post by lidex on 2010-04-23
szaemon  	
If your only sound device is onboard, re-enable it in the bios (Audio Controller)and then again:
```

aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by szaemon on 2010-04-26
Hi lidex,
Thanks again for your assistance.

I have re-enabled Audio Controller in my BIOS (though I'm not sure why it was disabled). 

And ran that code again:

```
me@mycomputer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
me@mycomputer:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
me@mycomputer:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC262

```

I wonder if I need to access the Extended BIOS

In the BIOS Utility under Advanced Chipset Settings, there is something called Intel (R) AMT BIOS Extension. I don't know what it is, but I have enabled it, though I can't access it.

Thanks Again,
szaemon

---

### Post by lidex on 2010-04-27
> **szaemon said:**
> Hi lidex,
Thanks again for your assistance.

I have re-enabled Audio Controller in my BIOS (though I'm not sure why it was disabled). 

And ran that code again:

```
me@mycomputer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
me@mycomputer:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
me@mycomputer:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC262

```

I wonder if I need to access the Extended BIOS

In the BIOS Utility under Advanced Chipset Settings, there is something called Intel (R) AMT BIOS Extension. I don't know what it is, but I have enabled it, though I can't access it.

Thanks Again,
szaemon

Do you have sound now?

---

### Post by szaemon on 2010-05-06
Nope. Still no sound. I guess I should have mentioned that. Whatever is wrong with the system and whatever that did(enabling Audio Controller in the BIOS) my PC's vow of silence continues...

---

### Post by lidex on 2010-05-06
Great now go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
And work through the troubleshooting steps. Make sure to install the alsa backports.

---

