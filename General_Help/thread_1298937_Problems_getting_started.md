---
title: "Problems getting started"
date: 2009-10-23
forum: General Help
---

### Post by danm91 on 2009-10-23
I have installed ubuntu to my laptop and have been having many problems, One while trying to install flash player to firefox comes up with this message:
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Also i appear to be getting no sound

---

### Post by Giblet5 on 2009-10-23
What version of Ubuntu did you install?

Did you install all of the updates, after the install, and before adding software? That's not required, but it's a swell idea.

---

### Post by danm91 on 2009-10-23
I have downloaded 9.04, how do i download updates because i think that this update program is failing to open

---

### Post by danm91 on 2009-10-23
I get the following error message when opening the update manager:


'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Giblet5 on 2009-10-23
> **danm91 said:**
> I have downloaded 9.04, how do i download updates because i think that this update program is failing to open

Click the System menu, select Administration, select Update Manager. Click the "Check" button. It will ask for your password. Give it.

"Check" will fetch the updated software lists and compare those to your current versions. When it's done checking, there will be a LOT of updates to install.

Click "Install Updates". It might tell you that you need to do a partial upgrade. That's OK, do it.

Once it starts downloading the updates, go to lunch because it will take a few minutes the first time. You will need to restart your PC when the updates have installed. Do that.

Are there any problems now?

---

### Post by danm91 on 2009-10-23
yes there are, look at my post above yours for the error code when i try opening the update manager

---

### Post by Giblet5 on 2009-10-23
> **danm91 said:**
> I get the following error message when opening the update manager:


'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Try this. Open a terminal window (Applications -> Accessories -> Terminal) and type the following:

```
sudo apt-get update
```

That will pull the latest package lists.

When it's done, type:

```
sudo apt-get upgrade -y
```

That's gonna take awhile and you'll need to restart when it's done.

---

### Post by danm91 on 2009-10-23
Did the first command, when i typed the second one i get this:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by Giblet5 on 2009-10-23
> **danm91 said:**
> Did the first command, when i typed the second one i get this:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

When did you download the 9.04 Ubuntu CD image? Today?

---

### Post by danm91 on 2009-10-23
I downloaded and installed last sunday

---

### Post by Giblet5 on 2009-10-23
> **danm91 said:**
> I downloaded and installed last sunday

Did you ever get the update manager to run?

What I'm trying to find out is, was there a bad CD image on the servers at some point. That would be bad.

---

### Post by danm91 on 2009-10-23
No i have never tried to get it to work, but i still have no sound and cannot get flash player to install so that i can watch videos on youtube

---

### Post by Giblet5 on 2009-10-23
> **danm91 said:**
> No i have never tried to get it to work, but i still have no sound and cannot get flash player to install so that i can watch videos on youtube

Let's get the software updated first, then we can get the sound and flash working. Deal?

What happens when you run this (terminal window): ```
sudo apt-get check
```

This updates the package cache and checks for unmet dependencies. Do you get an error?

If not, try the update, then upgrade steps again: ```
sudo apt-get update
sudo apt-get upgrade -y
```

---

### Post by danm91 on 2009-10-23
daniel@daniel-laptop:~$ sudo apt-get check
[sudo] password for daniel: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


daniel@daniel-laptop:~$ sudo apt-get upgrade -y
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by Giblet5 on 2009-10-23
> **danm91 said:**
> daniel@daniel-laptop:~$ sudo apt-get check
[sudo] password for daniel: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


daniel@daniel-laptop:~$ sudo apt-get upgrade -y
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


OK, let's force it to be clean. Again from a terminal window:
```
sudo rm -f /var/lib/apt/lists/*
sudo apt-get update
```

Then try the upgrade again: ```
sudo apt-get upgrade -y
```

---

### Post by danm91 on 2009-10-23
Thankyou very much for your time it is now updating :D

---

### Post by Giblet5 on 2009-10-23
> **danm91 said:**
> Thankyou very much for your time it is now updating :D

We'll fix the flash and sound problems when it's done and you've rebooted.

---

### Post by danm91 on 2009-10-23
I have done the updates got flash to work but am still getting no sound

---

### Post by Giblet5 on 2009-10-23
> **danm91 said:**
> I have done the updates got flash to work but am still getting no sound

I love the terminal window... What's the output of ```
sudo lspci
```

---

### Post by danm91 on 2009-10-23
daniel@daniel-laptop:~$ sudo lspci
[sudo] password for daniel: 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Giblet5 on 2009-10-23
OK, Ubuntu sees the sound controller on your chipset.

That's the tough part and it's done.

Please click on the System menu -> Preferences -> Sound

On "Playback Devices", see if you have an option for that Intel ICH7 audio controller.

Select that explicitly. (instead of automatic)

Try playing a video with sound.

---

### Post by danm91 on 2009-10-23
I dont have that option i do have other intels though

---

### Post by Giblet5 on 2009-10-23
> **danm91 said:**
> I dont have that option i do have other intels though

Make sure the sound *should* be audible (click the speaker icon and increase the volume to max).

Try each of them while playing a video with sound.

(You'll have to exit/restart Firefox for each test)

---

### Post by P4man on 2009-10-23
ensure the PCM mixer isnt muted. In the volume control, make sure you enable all sliders and move PCM to the top. 


Alternatively, run 

> alsamixer

in a terminal and using the arrow keys, adjust the volime of all relevant sliders, especially note the PCM one.
**edit**: and test sound in something else as flash in firefox as that might be yet another problem

---

### Post by danm91 on 2009-10-23
Everything is still not working :(

---

### Post by P4man on 2009-10-23
System menu -> Preferences -> Sound

what is the **default mixer tracks** set to ? Make sure its set to a *playback* device, and either alsa or pulse. And select MASTER below it

---

### Post by Giblet5 on 2009-10-23
> **danm91 said:**
> Everything is still not working :(

Has this PC ever before produced working sound?

Sound is a difficult thing to troubleshoot for some volunteer geek like me who doesn't have the option of crawling around and tracing wires...

Examples of why: Do you have speakers plugged in to the sound card's output? Are the speakers turned on? Do the speakers work when plugged in to an ipod? Are you plugging the speakers into the correct audio jack on the sound card? Is that jack color-coded? What color jack are you plugging the speakers into? Are you trying to use headphones? Where are you plugging them in? Are you sure that jack really should produce headphone level output? Do you wear a hearing aid? When did you last replace the hearing aid's batteries?...

I really can go on and on with that stuff...

---

### Post by danm91 on 2009-10-23
still nothing happening

---

### Post by danm91 on 2009-10-23
Ok, im using a laptop, the sound woked through the laptop speakers when i was running vista but since moving to ubuntu i have heard no sound

---

### Post by P4man on 2009-10-23
something else to try:
open a terminal and type:

```
sudo apt-get install pavucontrol
```

Now play a song or something. then go to applications > sound and video > pulse audio volume control

Do you see any "volune meters" active in the playback tab?
If you do, check the output device tab. whats there? 
Cant give you exact instructions as I dont have 9.04 here, but look around in that panel.

---

### Post by danm91 on 2009-10-23
There is a sound bar moving in there which must be good, just cant find anything in there thats will make it work

---

### Post by Giblet5 on 2009-10-23
[Here's the thread]("http://ubuntuforums.org/showthread.php?p=8139641") where this has been solved for many.

---

### Post by P4man on 2009-10-23
You're probably overlooking something trivial. But that just as hard to find as something difficult lol.

perhaps you can start making a few screenshots of  

system > prefences >sound
alsamixer

and post the output of 
```
 aplay -L
```

Hint, to easy make, upload and post screenshots, install Shutter from add/remove programs. Launch shutter from applications > Accessories. Then click  the third icon in shutter to make a screenshot of a single window. After you made the screenshot, right click it and chose upload. Then click the button to copy the link location and paste it in your post here. Takes less than 10s that way.

---

### Post by georgelenzer on 2009-10-23
I had a similar problem with my new HP laptop last week after installing Ubuntu Studio for the first time.  I have the ICH9 chipset which provides hardware that the system selects the 'intel_hda' ALSA sound device module (driver) for.  Everything was acting like it was working, but I heard nothing.  Some searching with Google revealed that I needed to add some info to **/etc/modprobe.d/alsa-base.conf**:

**options snd-hda-intel model=hp-m4**

This is specific to my model of laptop.  It won't necessarily work for yours.  It might help to post the make/model of laptop you have so specifics about the ALSA module options might be easier to find.

First we need to figure out which module your system is using for the sound device.  Since you're ICH7, it might be safe to assume that you're still using the snd-hda-intell module.  Get a list of your modules and repost them here using the following command:

```
lsmod
```

With that, we might be able to see if you need to modify your alsa-base.conf file as well.


Here is the thread that solved my problem, but it was specific to the HP HDX16 laptop:

[http://ubuntuforums.org/showthread.php?t=1238926](http://ubuntuforums.org/showthread.php?t=1238926)

---

### Post by georgelenzer on 2009-10-23
This is a fair approach if Pulse is not working well.  But I'm not convinced that the ALSA configuration is quite right.  I'd hesitate taking this approach until everything else has been tried.  Pulse is a rather nice upgrade away from Esound.

> **Giblet5 said:**
> [Here's the thread]("http://ubuntuforums.org/showthread.php?p=8139641") where this has been solved for many.

---

### Post by danm91 on 2009-10-23
daniel@daniel-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
isofs                  39844  1 
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
i915                   67844  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435252  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  4 snd_hda_intel,snd_pcm_oss
arc4                    9856  2 
ecb                    10752  2 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
pcmcia                 44748  0 
snd_seq_midi           14336  0 
ath5k                 107520  0 
snd_rawmidi            29696  1 snd_seq_midi
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
mac80211              217592  1 ath5k
psmouse                61972  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
video                  25872  0 
asus_laptop            24440  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  4 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13444  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
output                 11008  1 video
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
pcspkr                 10496  0 
led_class              12036  2 ath5k,asus_laptop
cfg80211               38288  2 ath5k,mac80211
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usb_storage            99648  2 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by georgelenzer on 2009-10-23
BTW... Here is a pretty good thread I just found for some other troubleshooting options with sound:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by georgelenzer on 2009-10-23
OK, below I've clipped out just the ALSA modules loaded on your system.  What is your laptop's make and model?  You have an hda_intel kernel module, same as mine.  So you might need to pass an option to it for the mixer to actually access the controls properly.  (It's still muted and your mixer isn't interfacing properly with the actual sound device)

> **danm91 said:**
> daniel@daniel-laptop:~$ lsmod
>snip<
snd_hda_intel         435252  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  4 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

---

### Post by danm91 on 2009-10-23
My laptop is a toshiba equium L40-10z

---

### Post by georgelenzer on 2009-10-23
I did a little digging and found that the audio chip in your laptop might be an ad1986a.  Pretty nice specs, does this look like the right machine?

[URL="http://eu.computers.toshiba-europe.com/innovation/product/Equium-L40-10Z/131897/DISC_MODEL/0/ACTION/PRINT_WITH_BACK/"]http://eu.computers.toshiba-europe.com/innovation/product/Equium-L40-10Z/131897/DISC_MODEL/0/ACTION/PRINT_WITH_BACK/
[/URL]
If so, I found this on the Ubuntu forums regarding that chip:

[http://ubuntuforums.org/showthread.php?t=259610](http://ubuntuforums.org/showthread.php?t=259610)

The '3stack' suggestion is similar to what I had to set up for my sound to work on my HP.  Try that out and see if anything happens.  If not, there is a small possility that the intel_hda module is not the right one.  I'll check the main ALSA project for info on the ad1986a chip if adding the '3stack' option changes nothing for you.

I'll check back later tonight and then later tomorrow for replies.  Monday would be the next time I'd be available.


> **danm91 said:**
> My laptop is a toshiba equium L40-10z

---

### Post by georgelenzer on 2009-10-23
Here is another link:

[http://ubuntuforums.org/showthread.php?t=159394](http://ubuntuforums.org/showthread.php?t=159394)

You might want to check and see if there are extra switches or sliders for other parts of the device and unmute or turn them up.  On my Gentoo workstation at work If I don't have the headphone and master volume sliders up or one of them is muted, there is no sound.

Sometimes the labels assigned to the controls is incorrect.  That can be fixed with module options as well, but... I'm not finding much about the ad1986a in the ALSA docs so far.  It does look like intel_hda may be correct based on some posts in other forums discussing the chip.

I'll continue to post anything else I find.

---

### Post by georgelenzer on 2009-10-23
More options to try for the intel_hda module (note comment #3):

[http://ubuntuforums.org/showthread.php?t=359117](http://ubuntuforums.org/showthread.php?t=359117)

---

### Post by georgelenzer on 2009-10-23
A little more info from your system when you have a chance... Run this:

sudo grep -i alsa /var/log/messages

You might need to do it after a fresh reboot if your laptop has been up for a while.  Hopefully that will show messages when your system loads the ALSA snd_* modules.  And possibly any related errors or config info.

Thanks

---

